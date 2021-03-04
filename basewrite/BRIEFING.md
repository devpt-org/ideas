# BASEWRITE

O propósito do basewrite é ser uma aplicação GitHub para complementar a área de documentação/especificação com todas as ligações possiveis no desenho, explicação, desempenho e timeline de um produto. A main feature será a produção de um livro de fácil leitura com todas as concepções descritas, permitindo a exportação da especificação em PDF.

As permissas que devem constar devem ser a simplicidade de produzir uma especificação e perceber o seu intuito, tarefas que foram agregadas, issues que foram associadas ao seu desenvolvimento, intervenientes e registos de commits. A diferenciação de timming entre os commits pode gerar um relatório mais macro sobre o tempo de desenvolvimento envolvido.

As tarefas num projeto GitHub seriam geradas automaticamente através da criação de épicos e dos devidos cenários no BaseWrite, à semelhança do que faz o Medium quando se comenta áreas de texto.

## Bases e inspirações

O próposito da aplicação é perfeitamente descrito no seguinte grupo de artigos, de leitura recomendada para que se perceba a solução e problemática envolvida:

- https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/
- https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/
- https://www.joelonsoftware.com/2000/10/04/painless-functional-specifications-part-3-but-how/
- https://www.joelonsoftware.com/2000/10/15/painless-functional-specifications-part-4-tips/

**Spec example:** https://www.joelonsoftware.com/whattimeisit/ (super clean)

## Adversários

- Confluence, mas não integra nada com github.
- specfox.com, tb não integra em nada com github e o editor deles é mero WYSIWYG.

Uma janela de oportunidade sem adversários nesta ârea.

## Pretensão

Uma imagem vale por mil palavras

![alt text](./spec-example.png "Spec example")

## Data

Entidades que poderam ser extrapuladas do exemplo acima para a criação da base de dados:

- Projecto (github)
- Descritivo (Prólogo)
- Épicos
  - Overview
  - Cenários
  - Objectivos e não objectivos
  - Especificação
    - Flow???
    - Historias (feature/screen)
    - Tarefas (to github)
  - ...github info

![alt text](./db-simple-example.png "DB example")

## Flow

O user instala aplicação no repo, para se interagir com a source code e todas as features que envolvem o repo. Do base write poder assinalar que partes da feature/screen irá criar tarefas no project do github. Todo o registo complementar de estado se encontra, se tem issues, PR e historico de commits bem como timeline de tempo de desenvolvimento deverá constar como extra management view de relatorio do épico.

![alt text](./flowchart-concept.jpg "Concept")

[Miro link](https://miro.com/welcomeonboard/1inwn1qPWKwqtdUkWaoac1yu0czSePaCDpMPaOscF4GwE6pMTIgrD5eU361yCCWX)

## Tecnologia

O uso de conceito REst, não necessáriamente multiplas bds e micro-serviços até ser uma unica db. Utilização de ferramentas já disponiveis para ajudar a rapidez de desenvolvimento nomeadamente:

- gotrue (centralized auth with audience and github integration) o meu fork com extras: https://github.com/websublime/gotrue
- gotrue-js (fe consumer): https://github.com/websublime/gotrue-js
- postgres with multiple batteries included: https://github.com/websublime/postgres
- courier: pubsub com hooks e preparado para events do postgres (realtime) bem como socket por topico: https://github.com/websublime/courier
- file server minio with auth (wrapper de minio com segurança e privacidade): https://github.com/websublime/barrel
- Hasura.io para api/graphql (superb)

Tudo isto são quase forks meus que tenho vindo a trabalhar para ajudar a construi uma infra-estrutura que dará para este e outros projectos. Courier quase finalizado e barrel também. Tudo dockers.

Linguagem de eleição para backend: golang. Frontend talvez Vue ou Angular.
