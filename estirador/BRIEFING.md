# Estirador

"Melhora uma vez, lança para todos"

O Estirador é um template em constante desenvolvimento, adaptável para as mais diversas linguagens, ferramentas e até para servir como base em projetos específicos de empresas.

Surgiu da necessidade de criar várias apps num reduzido espaço de tempo, algumas nos mesmos mercados, e em paralelo, manter as apps antigas já lançadas estáveis e com as últimas melhorias e correções que vão sendo desenvolvidas em diversos módulos comuns nos projectos mais recentes.

## Bases e inspirações

- <https://git-scm.com/docs/git-remote>

## Concorrência

- Copy / paste de código
- Geradores de boilerplate que geram o código uma vez
- Bibliotecas de código partilhado criadas pelas próprias empresas

## Flow

- O utilizador clona o projecto `estirador`, mas dá um nome diferente à pasta do projecto, neste caso _your-project-name_: `git clone ssh://xxx@xxx/estirador.git your-project-name`
- O utilizador remove o `git remote` do `estirador` e adiciona o do repositório do novo projecto
- O utilizador constrói o projecto
- Pontualmente, o utilizador corre o comando `update-project-boilerplate.sh` para atualizar a base técnica do projecto com a distribuição padrão do `estirador` ou um outro boilerplate empresarial baseado no sistema do `estirador`

> O flow apresentado acima é semelhante ao de criar um _fork_ de um repositório no Github. A diferença é que este workflow é baseado do uso de  `git remotes`, o que permite criar _forks_ mas entre qualquer provider de _git_.

## Tecnologia

### Necessárias
- Git

### Opcionais, incluídas na distribuição padrão
- NestJS (não confundir com NextJS)
- Webpack
- Docker
- Gatsby
- React
- Typescript
- Jest
- ESLint
- Prettier
