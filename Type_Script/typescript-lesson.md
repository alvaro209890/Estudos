# Aprendendo TypeScript do Zero

Bem-vindo ao guia completo para aprender TypeScript do zero! Este tutorial é projetado para iniciantes absolutos, guiando você passo a passo através dos conceitos fundamentais da linguagem. Vamos começar instalando as ferramentas necessárias e progredir para tópicos mais avançados, com desafios práticos ao longo do caminho.

## Pré-requisitos

Antes de começarmos, você precisa de:
- Um computador com Windows
- Acesso à internet para downloads
- Um editor de texto (recomendamos VS Code)

## Passo 1: Instalando Node.js

TypeScript roda no Node.js, então primeiro precisamos instalá-lo.

1. Acesse [nodejs.org](https://nodejs.org)
2. Baixe a versão LTS (recomendada para a maioria dos usuários)
3. Execute o instalador e siga as instruções padrão
4. Abra o PowerShell e verifique a instalação:
   ```bash
   node --version
   npm --version
   ```

**Desafio 1:** Instale o Node.js e confirme que ambos os comandos acima mostram versões válidas.

## Passo 2: Instalando TypeScript

Agora vamos instalar o compilador TypeScript globalmente.

1. No PowerShell, execute:
   ```bash
   npm install -g typescript
   ```
2. Verifique a instalação:
   ```bash
   tsc --version
   ```

**Desafio 2:** Instale o TypeScript e confirme que o comando `tsc --version` funciona.

## Passo 3: Configurando o Projeto

Vamos criar uma pasta para nosso projeto de aprendizado.

1. Crie uma nova pasta chamada `typescript-aprendizado`
2. Navegue até ela no PowerShell:
   ```bash
   mkdir typescript-aprendizado
   cd typescript-aprendizado
   ```
3. Inicialize um projeto Node.js:
   ```bash
   npm init -y
   ```
4. Instale TypeScript localmente (opcional, mas recomendado):
   ```bash
   npm install --save-dev typescript
   ```
5. Crie um arquivo `tsconfig.json`:
   ```json
   {
     "compilerOptions": {
       "target": "ES2020",
       "module": "commonjs",
       "strict": true,
       "esModuleInterop": true,
       "skipLibCheck": true,
       "forceConsistentCasingInFileNames": true
     }
   }
   ```

**Desafio 3:** Crie a estrutura do projeto conforme descrito acima e verifique se o arquivo `tsconfig.json` foi criado corretamente.

## Passo 4: Seu Primeiro Programa TypeScript

Vamos escrever nosso primeiro código TypeScript.

1. Crie um arquivo `hello.ts`:
   ```typescript
   console.log("Olá, TypeScript!");
   ```
2. Compile o código:
   ```bash
   tsc hello.ts
   ```
3. Execute o JavaScript gerado:
   ```bash
   node hello.js
   ```

**Desafio 4:** Crie o arquivo `hello.ts`, compile-o e execute-o. Modifique a mensagem para "Meu primeiro programa em TypeScript!".

## Passo 5: Tipos Básicos

TypeScript adiciona tipos estáticos ao JavaScript. Vamos explorar os tipos fundamentais.

### Tipos Primitivos

```typescript
// String
let nome: string = "João";

// Number
let idade: number = 25;

// Boolean
let ativo: boolean = true;

// Array
let hobbies: string[] = ["ler", "programar", "correr"];

// Tuple
let coordenadas: [number, number] = [10, 20];

// Enum
enum Cor {
  Vermelho,
  Verde,
  Azul
}
let corFavorita: Cor = Cor.Verde;

// Any (evite usar)
let qualquerCoisa: any = "pode ser qualquer tipo";

// Void (para funções que não retornam nada)
function logMensagem(): void {
  console.log("Mensagem logada");
}
```

**Desafio 5:** Crie um arquivo `tipos.ts` com variáveis de cada tipo acima. Use `console.log` para imprimir cada variável. Compile e execute.

## Passo 6: Funções

Funções em TypeScript podem ter tipos para parâmetros e retorno.

```typescript
function somar(a: number, b: number): number {
  return a + b;
}

function saudar(nome: string, idade?: number): string {
  if (idade) {
    return `Olá, ${nome}! Você tem ${idade} anos.`;
  }
  return `Olá, ${nome}!`;
}

// Função arrow
const multiplicar = (a: number, b: number): number => a * b;

// Função com parâmetros rest
function somarTudo(...numeros: number[]): number {
  return numeros.reduce((total, num) => total + num, 0);
}
```

**Desafio 6:** Crie um arquivo `funcoes.ts` com as funções acima. Teste cada uma com `console.log`. Adicione uma função que calcula a média de um array de números.

## Passo 7: Interfaces e Tipos

Interfaces definem a estrutura de objetos.

```typescript
interface Pessoa {
  nome: string;
  idade: number;
  email?: string; // opcional
}

function criarPessoa(nome: string, idade: number): Pessoa {
  return { nome, idade };
}

interface Animal {
  nome: string;
  fazerSom(): void;
}

class Cachorro implements Animal {
  nome: string;
  
  constructor(nome: string) {
    this.nome = nome;
  }
  
  fazerSom(): void {
    console.log("Au au!");
  }
}
```

**Desafio 7:** Crie um arquivo `interfaces.ts` com a interface `Pessoa` e uma função que cria pessoas. Implemente também a interface `Animal` com uma classe `Gato` que faz "Miau!".

## Passo 8: Classes

Classes em TypeScript são similares às de outras linguagens OOP.

```typescript
class Carro {
  private marca: string;
  private modelo: string;
  public ano: number;
  
  constructor(marca: string, modelo: string, ano: number) {
    this.marca = marca;
    this.modelo = modelo;
    this.ano = ano;
  }
  
  public getDescricao(): string {
    return `${this.marca} ${this.modelo} (${this.ano})`;
  }
  
  public static criarCarroPadrao(): Carro {
    return new Carro("Toyota", "Corolla", 2020);
  }
}

// Herança
class CarroEletrico extends Carro {
  private autonomia: number;
  
  constructor(marca: string, modelo: string, ano: number, autonomia: number) {
    super(marca, modelo, ano);
    this.autonomia = autonomia;
  }
  
  public getAutonomia(): number {
    return this.autonomia;
  }
}
```

**Desafio 8:** Crie um arquivo `classes.ts` com as classes acima. Instancie objetos e chame seus métodos. Adicione uma propriedade `cor` à classe `Carro`.

## Passo 9: Genéricos

Genéricos permitem criar componentes reutilizáveis.

```typescript
function identidade<T>(arg: T): T {
  return arg;
}

class Pilha<T> {
  private elementos: T[] = [];
  
  push(elemento: T): void {
    this.elementos.push(elemento);
  }
  
  pop(): T | undefined {
    return this.elementos.pop();
  }
  
  isEmpty(): boolean {
    return this.elementos.length === 0;
  }
}

interface ApiResponse<T> {
  data: T;
  sucesso: boolean;
  mensagem?: string;
}
```

**Desafio 9:** Crie um arquivo `genericos.ts` com os exemplos acima. Teste a classe `Pilha` com strings e números. Crie uma função genérica que encontra o maior elemento em um array.

## Passo 10: Módulos

TypeScript suporta módulos ES6.

```typescript
// matematica.ts
export function somar(a: number, b: number): number {
  return a + b;
}

export const PI = 3.14159;

// main.ts
import { somar, PI } from './matematica';

console.log(somar(5, 3)); // 8
console.log(PI); // 3.14159
```

**Desafio 10:** Crie os arquivos `matematica.ts` e `main.ts` conforme acima. Compile e execute `main.ts`. Adicione mais funções matemáticas ao módulo.

## Conclusão

Parabéns! Você completou os fundamentos do TypeScript. Pratique os desafios e explore mais na documentação oficial: [typescriptlang.org](https://www.typescriptlang.org/).

Próximos passos:
- Explore tipos avançados (union, intersection)
- Aprenda sobre decorators
- Integre com frameworks como Express ou React
- Configure um projeto com bundlers como Webpack

Continue praticando e construindo projetos!