# Nomenclatura Dev

Guia prático para nomear **variáveis, métodos, classes, interfaces e arquivos** de forma mais clara e previsível em projetos de software.

A proposta deste repositório é servir como uma referência rápida para quem trabalha com **TypeScript/JavaScript**, especialmente em projetos que usam conceitos de **Clean Architecture, Arquitetura Hexagonal, DDD e CQRS**.

## 📘 Guia completo em PDF

O material completo está disponível aqui:

➡️ [Abrir o Guia Prático de Nomenclatura para Código](./docs/guia-pratico-nomenclatura-codigo.pdf)

O PDF possui **sumário clicável** e exemplos práticos para consulta.

## O que o guia aborda

- Variáveis e constantes
- Métodos e funções
- Booleanos
- IDs, datas, coleções e quantidades
- Argumentos de construtor
- Entidades
- Value Objects
- Use Cases
- Controllers
- DTOs
- Repositories
- Gateways
- Strategies
- Observers
- Factories
- Presenters
- Services
- Mappers
- Validators
- Commands e Queries
- Handlers
- Eventos
- Errors
- Arquivos de infraestrutura

## Ideia principal

Um bom nome deve revelar a intenção do código sem exigir que outra pessoa abra a implementação para descobrir o que aquilo faz.

Por exemplo:

```ts
const data = await repository.find(id);
```

é menos informativo que:

```ts
const product = await productRepository.findById(productId);
```

A mesma lógica vale para classes.

Evite nomes genéricos como:

```ts
ProductManager
ProductHelper
ProductUtils
```

Prefira nomes que expressem uma responsabilidade concreta:

```ts
ProductPriceCalculator
ProductValidator
ProductFactory
ProductMapper
```

## Convenções rápidas

| Contexto | Padrão | Exemplo |
| --- | --- | --- |
| Entidade | substantivo do domínio | `Product` |
| Value Object | conceito/valor | `Email`, `Money` |
| Use Case | verbo + objeto | `CreateProduct` |
| Controller | recurso + Controller | `ProductController` |
| Repository | entidade + Repository | `ProductRepository` |
| Gateway | serviço/recurso + Gateway | `PaymentGateway` |
| Strategy | comportamento + Strategy | `DiscountStrategy` |
| Observer | evento observado | `OrderCreatedObserver` |
| DTO | intenção + DTO | `CreateProductDTO` |
| Presenter | recurso + Presenter | `ProductPresenter` |
| Factory | objeto + Factory | `ProductFactory` |
| Mapper | objeto + Mapper | `ProductMapper` |
| Validator | alvo/regra + Validator | `ProductValidator` |
| Command | verbo + objeto + Command | `CreateProductCommand` |
| Query | intenção + Query | `FindProductByIdQuery` |
| Error | condição + Error | `ProductNotFoundError` |

## Exemplos

### Variáveis

Evite:

```ts
const data = ...
const value = ...
const result = ...
const obj = ...
```

Prefira:

```ts
const product = ...
const activeProducts = ...
const authenticatedUser = ...
const totalProducts = ...
```

### Booleanos

Nomes booleanos devem parecer perguntas:

```ts
const isActive = true;
const hasPermission = true;
const canDelete = false;
const shouldRetry = true;
```

### Métodos

Métodos normalmente devem começar com um verbo:

```ts
createProduct()
findProductById()
calculatePrice()
sendEmail()
validatePassword()
```

### Contrato e implementação

Uma interface pode representar o contrato:

```ts
interface ProductRepository {
  findById(id: string): Promise<Product | null>;
}
```

E a infraestrutura deixa explícita a tecnologia utilizada:

```ts
class PrismaProductRepository implements ProductRepository {}
```

## Regra útil

> Se é difícil dar um nome específico para uma classe, talvez ela esteja assumindo responsabilidades demais.

Nomes como `Manager`, `Helper`, `Utils` e `Service` podem esconder responsabilidades diferentes dentro da mesma classe. Sempre que possível, prefira um nome que diga exatamente o papel daquele componente.

---

Material criado como referência prática para desenvolvimento e organização de código.
