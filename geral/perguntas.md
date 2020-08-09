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
