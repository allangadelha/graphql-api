## GRAPHQL

### Fontes:

01 - GraphQL - Dicionário do Programador - https://www.youtube.com/watch?v=xbLpIhCsIdg

02 - GraphQL - Página oficial - https://graphql.org/

03 - Entendendo o que é GraphQL através de exemplos - https://blog.codecasts.com.br/entendendo-o-que-%C3%A9-graphql-atrav%C3%A9s-de-exemplos-c2fa35e8bf63

04 - GraphQL: Pra que serve, Conceitos e Hello World - https://www.youtube.com/watch?v=7RoHxSGVAdU

05 - GraphQL aplicado no Node.js | Diego Fernandes - https://www.youtube.com/watch?v=oD8GqurXZ-0

#### Conceitos:

- usados no desenvolvimento de APIs;
- permite que uma API possa retornar mais ou menos dados;
- relacionamentos de acordo com a necessidade;
- performance é melhor que as APIs tradicionais;
- semelhante ao JSON;
- descritivo de dados é semelhante a Orientação a Objetos;
- você tem liberdade para defiir qual a estrutura dos seus dados;
- utiliza o conceito de herança usando "interfaces";

### EXEMPLO 01

#### Modelos de dados:

type Project { // tipo de dados
	// aqui contém três atributos
	name: String // atributo "name" do tipo string
	tagline: String // atributo "tagline" do tipo string
	contributors: [User] // enum "contributors" do tipo user
}

#### Modelos de consulta:

{
	project(name: "GraphQL") {
		tagline
	}
}

#### Resultado de consulta:

{
	"project": {
		"tagline": "A query language for APIs"
	}
}

### EXEMPLO 02

Enum Anunciantes {GOOGLE, IBM, MICROSOFT, AMAZON, B2W}

interface Publicacao { // criando "interfaces" "Publicacao"
	id: String! // atributo "id" do tipo String e obrigatório (por ter a "!" no final)
	nome: String // atributo "nome" do tipo String
	paginas: Int // atributo "Int" do tipo int
}

type Revista implements Publicacao { //tipo de dados "Revista" que implementa a interface "Publicacao"
	id: String! // atributo "id" do tipo String e obrigatório (por ter a "!" no final)
	nome: String // atributo "nome" do tipo String
	paginas: Int // atributo "Int" do tipo int
	anunciantes: [Anunciantes]
}

type Jornal implements Publicacao { //tipo de dados "Jornal" que implementa a interface "Publicacao"
	id: String! // atributo "id" do tipo String e obrigatório (por ter a "!" no final)
	nome: String // atributo "nome" do tipo String
	paginas: Int // atributo "Int" do tipo int
	anunciantes: [Anunciantes]
}

type Livro implements Publicacao { //tipo de dados "Livro" que implementa a interface "Publicacao"
	id: String! // atributo "id" do tipo String e obrigatório (por ter a "!" no final)
	nome: String // atributo "nome" do tipo String
	paginas: Int // atributo "Int" do tipo int
}

### Diferenças do REST

- o filtro do GraphQL é melhor implementado que no REST;
- a URL do REST é mais complexa por usar muito "Nesting"; no GraphQL não;
- no REST existe o "Overfetching" que devolve mais dados do que o necessário; no GraphQL só é retornado o necessário;
- no REST, quando a estrutura de dados é mais complexa são realizadas mais requisições HTTP; no GraphQLsó é retorado o que é requisitado;
- no GraphQL para modificações de dados o GrahQL utiliza mutation;
- no GraphQL toda query pode ser implementada para realizar uma escrita de dados;
- no GraphQL libs para várias linguagens de programação;
- permite multiplas querys em uma única requisição (deixando a aplicação mais performática);
- bibliotecas próprias que auxiliam no desenvolvimento;
- ao invés dos métodos tradicionais (GET, POST, PUT, DELETE), são utlizados apenas 03:
	- QUERY: retornar dados, a exemplo do GET no utilização de REST;
	- MUTATION: criar, alterar e deletar informação (POST, PUT e DELETE utilizados no REST);
	- SUBSCRIPTION: para oubir informação em tempo real (real-time nativo);
- mais "responsabilidade" para o front-end (autonomia  de controle de dados para o front-end);

### Características do GraphQL

- ID: representa a "chave primária" do "type" (tipo);
- é possível realizar aninhamento de "types";
- schema: funcionam como "rotas";
- resolvers: funcionam como "controllers";
- Playground: interface visual que auxilia no desenvolvimento (IDE do GraphQL);
- no Playground são geradas documentações com base no que é criado na aplicação:
	- aba Docs: documentação de Querys e Mutations definidas na aplicação e disponíveis para uso;
	- aba Schema: código da aplicação;
