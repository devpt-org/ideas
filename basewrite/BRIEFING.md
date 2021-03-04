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

## Concorrência

### Análise
#### Confluence

- É provavelmente o maior player do mercado no que toca a documentação e especificações
- Não tem integração direta com GitHub à exceção de integrações com addons, p.ex.:
  - [Github links for Confluence](https://marketplace.atlassian.com/apps/1216106/github-links-for-confluence?hosting=cloud&tab=overview)
  - [Git for Confluence](https://marketplace.atlassian.com/apps/1211675/git-for-confluence?hosting=server&tab=overview)
  - [Github Macros for Confluence](https://marketplace.atlassian.com/apps/1216734/github-macros-for-confluence?hosting=cloud&tab=overview)
  
    Permitem linkar ítens do GitHub (repositórios, issues, PRs, branches, etc) mas não permitem criação de nada no GitHub a partir das plataformas.
    
#### Specfox.com
- Tem vários pontos em comum com a nossa spec e pode ser um ponto de interesse para analisarmos o UX. Como grande desvantagem, não integra em nada com GitHub e o seu editor é meramente WYSIWYG - o que podemos usar como nossa vantagem, caso usemos p.ex. Markdown e permitir uma edição mais visual para utilizadores não técnicos.
    
#### Tray.io
- Permite a criação de Workflows entre a plataforma deles e o GitHub, mas não é claro que tipo de ações permite.

### Conclusão
Depreende-se da análise anterior, que existe uma janela de oportunidade, sem concorrência de peso neste nicho.

## Aspiração

A descrição dum Spec gerado numa imagem:

![Spec example](./spec-example.png "Spec example")

## Data

Entidades que puderam ser extrapuladas do exemplo acima para a criação da base de dados:

- Projecto (GitHub)
- Descritivo (Prólogo)
- Épicos
  - Overview
  - Cenários
  - Objectivos e não objectivos
  - Especificação
    - Flow
    - Histórias (feature/screen)
      - Notas Técnicas 
    - Tarefas (a serem sincronizadas com o GitHub)
  - Dados relacionados no GitHub
    - Repositórios
    - Pull Requests
    - Commits
    - Branches
    - Issues
    - Utilizadores
    - Projetos
    - Tarefas nos Boards

![alt text](./db-simple-example.png "DB example")
[Miro link to edit DB schema](https://miro.com/welcomeonboard/1inwn1qPWKwqtdUkWaoac1yu0czSePaCDpMPaOscF4GwE6pMTIgrD5eU361yCCWX)

## Flow

1) O utilizador instala uma aplicação GitHub com permissão de escrita e leitura no repositório (para que seja possível criar e sincronizar issues e outro tipo de conteúdos)
2) No BaseWrite o utilizador escolhe que partes da Feature/Screen criará tarefas no projeto do GitHub

No épico, existirá uma view de extra management que permitirá aceder a informação relativa ao estado, issues, PRs, histórico de commits e timeline de tempo de desenvolvimento.

![alt text](./flowchart-concept.jpg "Concept")

## Tecnologia

O uso de conceito REST, não necessariamente múltiplas bds e micro-serviços até ser uma única db. Utilização de ferramentas já disponiveis para ajudar a rapidez de desenvolvimento nomeadamente:

- gotrue (centralized auth with audience and GitHub integration) o meu fork com extras: https://github.com/websublime/gotrue
- gotrue-js (fe consumer): https://github.com/websublime/gotrue-js
- postgres with multiple batteries included: https://github.com/websublime/postgres
- courier: pubsub com hooks e preparado para events do postgres (realtime) bem como socket por topico: https://github.com/websublime/courier
- file server minio with auth (wrapper de minio com segurança e privacidade): https://github.com/websublime/barrel
- Hasura.io para api/graphql (superb)

Tudo isto são quase forks meus que tenho vindo a trabalhar para ajudar a construir uma infra-estrutura que dará para este e outros projectos. Courier quase finalizado e barrel também. Tudo dockers.

Linguagem de eleição para backend: golang. Frontend talvez Vue ou Angular.
