# Perguntas

## Aula 1

1 - Quais das afirmações abaixo representam uma vantagem da adoção de integração contínua no desenvolvimento de software?

- __Agregar todo o processo de construção de artefatos, controle de qualidade e entrega de software em um fluxo contínuo e transparente para todos os envolvidos__
- __Melhora na cobertura de qualidade do código do projeto, visto que é possível analisar o produto durante o processo de construção__
- Os times vão trabalhar em silos, focando exclusivamente na qualidade de entrega das suas tasks diárias, reduzindo assim o re-trabalho
- __Diminuição do time to market na entrega do produto para o mercado__

2 - Durante o curso usaremos o Jenkins como ferramenta principal, mas o que é Jenkins?

- __Um servidor de integração continua.__
> Alternativa correta! O Jenkins é um servidor de Integração Contínua open-source escrito em Java. Ele é o mais popular mas não a única opção. Outros servidores de *Integração Contínua * são TeamCity, Bamboo, Travis CI ou Gitlab CI entre vários outros.

- Uma ferramenta que permite o monitoramento de tarefas de maneira ágil.
- Uma ferramenta de build (construção de pacote)

3 - O ponto inicial da nossa Pipeline de integração continua é o repositório GIT que hospedamos no Github.
Das alternativas abaixo, assinale aquela que aponta o fluxo correto de um versionamento inicial de um código-fonte com o Git:

- git init --> git push origin master --> git add . --> git remote add origin git@github.com:<seu-usuario>/jenkins-todo-list.git --> git pull
- git init --> git clone -m "Meu primeiro commit" --> git push origin master
- __git init --> git add . --> git commit -m "Meu primeiro commit" --> git remote add origin git@github.com:<seu-usuario>/jenkins-todo-list.git --> git push origin master__
> Alternativa correta! Esse é o fluxo básico é:
> 
> ``` bash
> init
> add e commit
> remote add
> push to master
> ```

4 - Qual a diferença entre o Git Log de consulta periódica e o log da Saída do console, em um job no Jenkins?

- O primeiro mostra o log do servidor do Jenkins, já o segundo mostra o log da execução do build do job
- __O primeiro mostra a consulta ao repositório do código-fonte, já o segundo mostra o log da execução do build do job__
> Alternativa correta! O primeiro log mostra as consultas periódicas, configuradas no job, ao repositório, e somente após alguma alteração ele vai prosseguir com o build, onde seus logs podem ser acessados pela Saída do console.

- O primeiro mostra o log da execução do build do job, já o segundo mostra a consulta ao repositório do código-fonte
- Eles são iguais, a única diferença é o local onde os acessamos

5 - Aprendemos que o Jenkins verifica periodicamente o repositório para encontrar mudanças no código e iniciar o build do Job.
Qual o repositório o Jenkins está verificando?

- O repositório local no computador.
- __O repositório remoto no Github.__
> Alternativa correta, pois configuramos o Github como repositório remoto que o Jenkins verifica periodicamente se há alterações no código.

- O repositório local do container docker
- O repositório remoto no Gitlab.

## Aula 2

1 - Sejam os seguintes comandos no build manual:
``` bash
python createsuperuser
python migrate
```
Qual a função deles, respectivamente?

- Criar o virtualenv para instalar as dependências
- Migrar as alterações dos seus modelos; criar o principal usuário para acessar a aplicação
- __Criar o principal usuário para acessar a aplicação; migrar as alterações dos seus modelos__

2 - No servidor onde o Docker está instalado, qual o arquivo que criamos para possibilitar o controle remoto do Docker?

- /var/systemd/system/docker.service.d/override.conf
- __/etc/systemd/system/docker.service.d/override.conf__
- /etc/systemd/system/docker.service.d/docker-override.conf
- /etc/init.d/system/docker.service.d/override.conf

3 - Na construção de imagens para o Docker, recomenda-se o uso de um linter. Por quê?

- __Para garantir a utilização das melhores práticas na criação de um Dockerfile__
- Com isso, garantimos que a imagem será registrada com sucesso no Docker Hub
- Pois com o linter, garantimos que todos os comandos serão executados corretamente

## Aula 3

1 - Considerando a abordagem utilizada para definir a configuração da aplicação nos ambientes de desenvolvimento e produção, escolha a alternativa que justifica tal escolha:

- Nada justifica tal escolha
- Apesar da escolha de separar os ambientes por arquivo de configuração, recomenda-se rodar os testes sistêmicos no banco de dados de produção
- __A abordagem escolhida permite que a mesma imagem construída no processo seja utilizada para testes, validações e também para rodar em produção, visto que o arquivo .env de cada ambiente é passado na execução do container__
- Seria mais interessante construir a imagem com o arquivo de configuração de ambiente

2 - Qual a vantagem de registrar a imagem no Docker Hub no início do pipeline?

- A principal vantagem é que a imagem com a aplicação 100% funcional estará sempre disponível
- __Que, após registrar a imagem, qualquer um com acesso ao domínio pode baixar e rodar a aplicação__
> Alternativa correta! Devemos construir somente uma vez a imagem no pipeline.

- Para garantir que o time de desenvolvimento não acesse o artefato construído para produção

## Aula 4

1 - Qual o caminho no Jenkins para instalação de plugins?

- Gerenciar Jenkins --> Gerenciar Plugins --> Instalados
- __Gerenciar Jenkins --> Gerenciar Plugins --> Disponíveis__
- Gerenciar Jenkins --> Configurar o sistema --> Nuvem

2 - Escolha a opção que melhor reflete o que é a linguagem Groovy:

- É a linguagem de programação recomendada para aplicações que serão construídas através de jobs no Jenkins.
- __É uma sintaxe que utilizamos para criar os nossos pipelines com código__
- No nosso exemplo, foi a linguagem utilizada na aplicação de todo-list.

## Aula 5

1 - Qual é a sintaxe correta para colocar uma decisão no pipeline, utilizando a linguagem Groovy?

- __A__
``` sh
timeout(time: 10, unit: 'MINUTES') {
    input(id: "Deploy Gate", message: "Deploy em produção?", ok: 'Deploy')
}
```

- B
``` sh
tout(time: 10, unit: 'MINUTES') {
    input(id: "Deploy Gate", message: "Deploy em produção?", ok: 'Deploy')
}
```

- C
``` sh
timeout(time: 10 'MINUTES') {
    input(id: "Deploy Gate", message: "Deploy em produção?", ok: 'Deploy')
}
```

- D
``` sh
time-outs(time: 10, unit: 'MINUTES') {
    input(id: "Deploy Gate", message: "Deploy em produção?", ok: 'Deploy')
}
```

2 - Qual é uma das vantagens de passar parâmetros de um job para outro no Jenkins?

- Essa é única maneira de habilitar o trigger de outros jobs automaticamente
- Isso possibilita que o Jenkins combine todos os jobs encadeados em um novo job com todos os passos
- __Com essa integração, alguns parâmetros podem ser passados para o primeiro job e os demais, quando configurados, podem receber automaticamente esses valores, como por exemplo o nome da imagem__

## Aula 6

1 - No último vídeo, conhecemos o Sonarqube. Dentre as alternativas abaixo, qual representa melhor a sua definição?

- É uma ferramenta que constrói pipelines
- É uma ferramenta que automaticamente identifica e corrige os code smells encontrados
- __É uma ferramenta que escaneia o código fonte para identificar débitos técnicos, más práticas, erros de sintaxe e outras métricas__
- É uma ferramenta que somente avalia o débito técnico de uma aplicação

2 - Qual o comando que faz a instalação do Sonarqube com Docker?

- apt-get install sonarcube
- __docker run -d --name sonarqube -p 9000:9000 sonarqube:lts__
- docker images -d --name sonarqube -p 9000:9000 sonarqube:lts

3 - Tendo o seguinte parâmetro do sonar-scanner:
``` bash
-Dsonar.login
```
Qual a sua função?

- É a senha que acompanha o nome do usuário sonar.login
- É útil apenas quando precisamos criar retroativamente o histórico de um projeto não analisado antes
- __É login ou token de autenticação de um usuário do SonarQube com permissão de execução de análise no projeto__
