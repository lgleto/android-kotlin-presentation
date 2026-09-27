# Learning Goals / Aquisição de Competências

Competências a adquirir nesta unidade, alinhadas com o conteúdo da apresentação e com os projectos de exemplo (Calculator, DailyNews, ShoppingList, motor de jogo).

## Metodologias

Esta disciplina será leccionada com uma forte componente prática, orientada à realização de projectos individuais e em grupo, tendo como principal objectivo incentivar a aprendizagem com base na experimentação e na colaboração, bem como na exploração e reutilização dos recursos existentes na Web.

## Demonstração da coerência das metodologias de ensino com os objetivos de ensino/aprendizagem da UC

A prossecução dos objectivos propostos passa por transmitir os conceitos teóricos dos principais temas da disciplina e, para cada um deles, aplicá-los na prática. Existe uma enorme dificuldade em aprender estes conceitos sem os experimentar e praticar; por isso, os alunos serão fortemente incentivados a pesquisar soluções para os problemas práticos propostos nas aulas. Serão ajudados a ultrapassar as barreiras que encontrem durante a resolução dos problemas, com apoio do docente, e no final serão propostas resoluções gerais para os problemas apresentados.

É por este motivo que a avaliação se faz por **aquisição de competências** verificada em contexto de aula (pequenos projectos e demonstrações práticas), e não por exame teórico. Numa disciplina centrada no desenvolvimento de aplicações móveis, o que importa é a capacidade do aluno fazer a arquitectura de uma aplicação, depurar e explicar soluções — competências que se demonstram fazendo, não memorizando. Um exame escrito sem computador não reflectiria o trabalho real da disciplina nem mediria, de forma fiável, se o aluno domina Compose, APIs, persistência ou arquitectura. Assim, a avaliação contínua e o trabalho de grupo substituem a necessidade de exame: o progresso e o domínio de cada competência são observados ao longo do semestre, à medida que os alunos resolvem os desafios práticos.

## Avaliação

A avaliação tem duas componentes: uma **em aula** e outra **extra-aulas**.

- **Aquisição de competências (AC)** — componente em aula, baseada nas competências demonstradas na sala de aula (pequenos projectos e práticas).
- **Trabalho prático (TP)** — componente extra-aulas, realizada em grupo. Inclui relatório escrito, implementação da solução e defesa oral.

A **avaliação final (AF)** é dada por:

```
AF = 50% × AC + 50% × TP
```

Ambas as componentes são obrigatórias e têm nota mínima de **9,5 valores**:

| Componente | Peso | Nota mínima |
|------------|------|-------------|
| Aquisição de competências (AC) | 50% | ≥ 9,5 |
| Trabalho prático (TP) | 50% | ≥ 9,5 |

---

## Composable UI

**Objectivo:** Construir interfaces Android com Jetpack Compose de forma declarativa.

O estudante deve ser capaz de:

- Explicar a diferença entre UI imperativa (Views/XML) e UI declarativa (Compose)
- Criar funções `@Composable` e integrá-las numa `Activity` com `setContent { }`
- Usar layouts básicos (`Column`, `Row`, `Box`) e componentes (`Text`, `Button`)
- Aplicar `Modifier` (tamanho, padding, alinhamento, fundo) com ordem correcta
- Gerir estado local com `remember` e `mutableStateOf`, compreendendo recomposição
- Usar `LaunchedEffect` para efeitos secundários (carregar dados, timers) sem bloquear a UI
- Pré-visualizar UI no Android Studio com `@Preview`

**Projecto de referência:** Calculator (Compose) e ecrãs da DailyNews.

---

## Functional Programming

**Objectivo:** Aplicar conceitos de programação funcional em Kotlin no contexto de apps Android.

O estudante deve ser capaz de:

- Tratar funções como valores (guardar, passar e devolver funções)
- Distinguir funções puras de código com efeitos secundários
- Usar funções de ordem superior e lambdas (ex.: callbacks em botões Compose)
- Preferir imutabilidade (`val`) e mapas de operações em vez de `when` duplicado
- Modelar comportamento da UI com tipos função, ex.: `(String) -> Unit`

**Projecto de referência:** `CalculatorBrain` (operações como mapa de funções) e `CalculatorButton` (callback injectado).

---

## Lists and Details

**Objectivo:** Implementar o padrão lista → detalhe em Compose.

O estudante deve ser capaz de:

- Mostrar coleções com `LazyColumn` e itens reutilizáveis (ex.: `RowArticle`)
- Modelar dados de domínio (ex.: `Article`) a partir de JSON ou fontes locais
- Navegar de um item da lista para um ecrã de detalhe com dados do item seleccionado
- Tratar estados de UI: loading, erro, lista vazia e sucesso
- Separar a linha da lista do ecrã de detalhe em Composables distintos

**Projecto de referência:** DailyNews (`HomeView` → `ArticleDetail`, `ReadLaterView`).

---

## Navigation

**Objectivo:** Estruturar navegação multi-ecrã com Navigation Compose.

O estudante deve ser capaz de:

- Definir rotas com `sealed class Screen` e um `NavHost` / `NavController`
- Organizar o ecrã com `Scaffold` (`topBar`, `bottomBar`, conteúdo)
- Implementar bottom navigation (`NavigationBar` + `NavigationBarItem`)
- Implementar top bar com título, botão voltar e acções (partilhar, bookmark)
- Distinguir ecrãs base e ecrãs de detalhe (`isBaseScreen`, `popBackStack`)
- Preservar selecção da bottom bar com `rememberSaveable`

**Projecto de referência:** DailyNews (Home, Technology, Sports, Bookmarks, Article).

---

## Web API — OkHttp

**Objectivo:** Consumir APIs REST em Android com OkHttp.

O estudante deve ser capaz de:

- Configurar a dependência OkHttp e a permissão `INTERNET`
- Construir e executar pedidos HTTP GET de forma assíncrona (`enqueue`)
- Processar respostas JSON e mapear para modelos Kotlin
- Expor o resultado à UI via ViewModel + `StateFlow` / `collectAsState`
- Tratar falhas de rede e códigos HTTP inesperados
- Evitar trabalho de rede na Main Thread

**Projecto de referência:** DailyNews + NewsAPI (`HomeViewModel.fetchArticles`).

---

## Gameloop

**Objectivo:** Compreender e implementar um loop de jogo em plataformas móveis (EDJD).

O estudante deve ser capaz de:

- Explicar o ciclo típico de um motor de jogo: input → update → render
- Relacionar o gameloop com o ciclo de vida da app Android (pause/resume)
- Gerir tempo, frames e actualização de estado do jogo sem bloquear a UI
- Separar lógica de jogo da apresentação
- Aplicar conceitos de Kotlin/Android (threads, estado, ciclo de vida) num contexto interactivo em tempo real

**Âmbito:** Desenvolvimento de motor de jogo para plataformas móveis (EDJD).

---

## Firebase

**Objectivo:** Usar Firebase como backend (BaaS) numa app Android.

O estudante deve ser capaz de:

- Configurar o projecto (`google-services.json`, BOM Firebase, plugins Gradle)
- Autenticar utilizadores com Firebase Auth (email/password) e usar `currentUser?.uid`
- Modelar dados em Cloud Firestore (collections, documents, subcollections)
- Ler e escrever dados (criar carrinhos, listar, actualizar campos)
- Usar listeners em tempo real (`addSnapshotListener`) para sincronizar UI entre dispositivos
- Associar dados ao utilizador autenticado (ex.: `owners` com `uid`)

**Projecto de referência:** ShoppingList (Auth + Firestore).

---

## Android Room

**Objectivo:** Persistir dados locais com Room (SQLite).

O estudante deve ser capaz de:

- Definir `@Entity`, `@Dao` e `@Database`
- Executar queries com `suspend` em `Dispatchers.IO`
- Inserir, ler e apagar registos (ex.: bookmarks / favoritos)
- Usar Room como cache offline complementar a dados remotos (OkHttp)
- Expor dados locais à UI através do ViewModel
- Compreender o padrão Singleton da base de dados

**Projecto de referência:** DailyNews bookmarks (`ArticleCache`, `ReadLaterView`).

---

## Clean Architecture

**Objectivo:** Organizar a app em camadas testáveis e desacopladas.

O estudante deve ser capaz de:

- Separar Presentation (Compose), ViewModel, Repository e Data Source
- Aplicar MVVM: a View observa estado; o ViewModel coordena; o Model/Repository acede a dados
- Encapsular Firebase/OkHttp/Room num Repository (a UI nunca chama a fonte directamente)
- Uniformizar resultados com wrappers de estado (Loading / Success / Error)
- Usar injecção de dependências com Dagger Hilt (`@HiltAndroidApp`, `@HiltViewModel`, `@Inject`, `@Module` / `@Provides`)
- Explicar os benefícios: testabilidade, troca de fontes de dados, Single Responsibility

**Projecto de referência:** ShoppingList (Hilt + `CartRepository` + ViewModels).

---

## Visão geral

| Competência              | Foco principal                         | App / exemplo        |
|--------------------------|----------------------------------------|----------------------|
| Composable UI            | UI declarativa Compose                 | Calculator, DailyNews |
| Functional Programming   | Funções, lambdas, imutabilidade        | Calculator           |
| Lists and Details        | `LazyColumn` + ecrã detalhe            | DailyNews            |
| Navigation               | Rotas, Scaffold, barras                | DailyNews            |
| Web API OkHttp           | HTTP REST + JSON                       | DailyNews / NewsAPI  |
| Gameloop                 | Loop de jogo e ciclo de vida           | Motor de jogo (EDJD) |
| Firebase                 | Auth + Firestore tempo real            | ShoppingList         |
| Android Room             | Persistência local SQLite              | DailyNews bookmarks  |
| Clean Architecture       | Camadas + Hilt + Repository            | ShoppingList         |
