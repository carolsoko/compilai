# Documentação - Compilador Portugol Modernizado

## Visão Geral
O Compilador Portugol Modernizado é uma aplicação completa que permite escrever e executar programas em Portugol (pseudocódigo em português) diretamente no navegador. É compatível com a sintaxe do VisualG, amplamente utilizado no ensino de programação no Brasil.

## Versão Atual
**Versão:** 2.0 (Agosto 2025)  
**Status:** Funcional e estável  
**Compatibilidade:** Navegadores modernos com suporte a ES6+

## Funcionalidades adicionadas nesta versão:

- **Operador MOD** para resto de divisão (x mod 3)
- **Função ABS** para valor absoluto (abs(x))
- **Função RAIZQ** para raiz quadrada (raizq(x))
- **Função QUAD** para elevar ao quadrado (quad(x))
- **Função COMPR** para comprimento de string (compr(texto))
- **Função MAIUSC** para converter maiúscula (maiusc(texto))
- **Função MINUSC** para converter minúscula (minusc(texto))
- **Comando INTERROMPA** para sair de laços


## Funcionalidades Principais

### 1. Interface de Usuário
- **Editor de Código:** Textarea com fonte monoespaçada para edição de código Portugol
- **Área de Saída:** Console escuro com saída em tempo real
- **Controles:**
  - Botão "Executar" para iniciar a execução
  - Botão "Limpar saída" para limpar o console
  - Checkbox "Debug" para ativação de logs detalhados
- **Layout Responsivo:** Grid de duas colunas adaptável

### 2. Tipos de Dados Suportados
- **inteiro:** Números inteiros
- **real:** Números decimais (ponto flutuante)
- **caractere:** Strings de texto
- **logico:** Valores booleanos (verdadeiro/falso)

### 3. Declaração de Variáveis
```portugol
// Variáveis simples
inteiro x, y, z
real nota1, nota2
caractere nome
logico aprovado

// Arrays unidimensionais
inteiro vetor[10]
real notas[5]

// Matrizes bidimensionais
inteiro matriz[3][4]
real tabela[2][5]
```

### 4. Estruturas de Controle

#### Condicional SE-ENTÃO-SENÃO
```portugol
se (condicao) entao
    // comandos
senao
    // comandos opcionais
fimse
```

#### Laços de Repetição

**REPITA-ATÉ:**
```portugol
repita
    // comandos
ate (condicao)
```

**ENQUANTO-FAÇA:**
```portugol
enquanto (condicao) faca
    // comandos
fimenquanto
```

**PARA:**
```portugol
para i de 1 ate 10 passo 1 faca
    // comandos
fimpara
```

#### Estrutura ESCOLHA-CASO
```portugol
escolha (variavel)
caso 1:
    // comandos
caso 2:
    // comandos
outrocaso
    // comandos padrão
fimescolha
```

### 5. Funções e Procedimentos

#### Funções (retornam valor)
```portugol
funcao nomeFuncao(parametro1, parametro2): tipoRetorno
    // corpo da função
    retorna valor
fimfuncao
```

#### Procedimentos (não retornam valor)
```portugol
procedimento nomeProcedimento(parametro1, parametro2)
    // corpo do procedimento
fimprocedimento
```

### 6. Entrada e Saída de Dados

#### Entrada
```portugol
leia(variavel)          // Variável simples
leia(array[indice])     // Elemento de array
leia(matriz[i][j])      // Elemento de matriz
```

#### Saída
```portugol
escreva("texto")        // Sem quebra de linha
escreval("texto")       // Com quebra de linha
escreval("Valor: ", x, " - Nome: ", nome)  // Múltiplos argumentos
```

### 7. Operadores Suportados

#### Aritméticos
- `+` (adição)
- `-` (subtração)
- `*` (multiplicação)
- `/` (divisão)

#### Relacionais
- `=` (igual)
- `<>` (diferente)
- `<` (menor que)
- `>` (maior que)
- `<=` (menor ou igual)
- `>=` (maior ou igual)

#### Lógicos
- `e` (AND/&&)
- `ou` (OR/||)
- `nao` (NOT/!)

### 8. Características Técnicas

#### Indexação de Arrays
- **1-based indexing:** Arrays e matrizes começam no índice 1 (como no VisualG original)
- Verificação automática de limites com mensagens de erro detalhadas

#### Sistema de Parsing
- **Parser recursivo:** Analisa a estrutura do código automaticamente
- **Tratamento de comentários:** Suporte a `//` e `{ }`
- **Análise de strings:** Processamento correto de aspas duplas e simples
- **Separação de argumentos:** Parsing inteligente de múltiplos parâmetros

#### Execução
- **Ambiente isolado:** Cada execução cria um ambiente limpo
- **Escopo de variáveis:** Funções têm escopo local, procedimentos acessam escopo global
- **Tratamento de erros:** Mensagens detalhadas em português
- **Recursão:** Suporte completo a funções recursivas

### 9. Sistema de Debug
Quando ativado, o debug mostra:
- AST (Árvore Sintática Abstrata) gerada
- Passos de execução detalhados
- Avaliação de expressões
- Conversão de operadores
- Processamento de argumentos

### 10. Exemplos Incluídos

#### Programa de Fatorial com Vetor
O interpretador inclui um exemplo completo que demonstra:
- Declaração de variáveis e arrays
- Função recursiva para cálculo de fatorial
- Procedimento para preenchimento de array
- Estruturas de repetição
- Entrada e saída formatada

### 11. Compatibilidade com VisualG

### Funcionalidades Compatíveis 
- Sintaxe completa de declarações
- Todas as estruturas de controle
- Funções e procedimentos
- Arrays uni e bidimensionais
- Operadores aritméticos, relacionais e lógicos
- Entrada via `leia()` e saída via `escreva()`/`escreval()`
- Comentários com `//` e `{ }`

### Diferenças da Implementação
- **Entrada:** Usa `prompt()` do navegador ao invés de interface específica
- **Tipos:** Conversão automática de tipos conforme necessário
- **Execução:** Client-side no navegador, não em ambiente desktop

## Requisitos do Sistema
- **Navegador:** Chrome, Firefox, Safari, Edge (versões recentes)
- **JavaScript:** ES6+ habilitado
- **Conectividade:** Não requerida (funciona offline após download)
- **Recursos:** Mínimos - funciona em qualquer dispositivo moderno

## Estrutura do Arquivo
- **HTML:** Interface e estrutura da aplicação
- **CSS:** Estilos responsivos e tema visual
- **JavaScript:** Motor completo de interpretação Portugol
- **Tamanho total:** ~50KB (arquivo único auto-contido)
