# Documentação - Compilador Portugol Modernizado

## Visão Geral
O Compilador Portugol Modernizado é uma aplicação completa que permite escrever e executar programas em Portugol (pseudocódigo em português) diretamente no navegador. É compatível com a sintaxe do VisualG, amplamente utilizado no ensino de programação no Brasil.

## Versão Atual
**Versão:** 1.0 (Agosto 2025)  
**Status:** Funcional e estável  
**Compatibilidade:** Navegadores modernos com suporte a ES6+

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

#### Funcionalidades Compatíveis 
- Sintaxe completa de declarações
- Todas as estruturas de controle
- Funções e procedimentos
- Arrays uni e bidimensionais
- Operadores aritméticos, relacionais e lógicos
- Entrada via `leia()` e saída via `escreva()`/`escreval()`
- Comentários com `//` e `{ }`

#### Funcionalidades IMPLEMENTADAS:
- Todos os tipos básicos (inteiro, real, caractere, logico)
- Arrays uni e bidimensionais com indexação 1-based
- Estruturas de controle completas (se, enquanto, para, repita, escolha)
- Funções e procedimentos com parâmetros
- Operadores relacionais e lógicos
- Entrada/saída básica
- Comentários e parsing robusto

### 12. Funcionalidades Faltantes:

#### Funções Matemáticas Nativas
- **abs(x)** - valor absoluto
- **exp(x)** - exponencial
- **ln(x)** - logaritmo natural
- **log(x)** - logaritmo base 10
- **raizq(x)** - raiz quadrada
- **quad(x)** - elevar ao quadrado
- **sin(x), cos(x), tan(x)** - funções trigonométricas
- **pi** - constante pi

#### Funções de String
- **compr(s)** - comprimento da string
- **maiusc(s)** - converter para maiúscula
- **minusc(s)** - converter para minúscula
- **copia(s, pos, qtd)** - substring
- **pos(substr, s)** - posição de substring
- **numpcarac(n)** - converter número para caractere
- **caracpnum(c)** - converter caractere para número

#### Funções de Conversão de Tipos
- **inttreal(x)** - inteiro para real
- **realtint(x)** - real para inteiro
- **inttcarac(x)** - inteiro para caractere
- **caracpint(x)** - caractere para inteiro

#### Operadores Adicionais
- **mod ou %** - operador módulo (resto da divisão)
- **div** - divisão inteira
- **^** - exponenciação

#### Estruturas Avançadas
- **interrompa** - quebra de laços (break)
- **algoritmo** - cabeçalho opcional do programa
- **var** - seção de declaração de variáveis
- **inicio/fim** - delimitadores do programa principal

#### Recursos de Depuração
- **timer** - cronômetro/temporização
- **aleatorio** - geração de números aleatórios

#### Arquivo/Persistência
- Funções de leitura/escrita de arquivos
- Persistência de dados entre execuções

## Prioridade para Implementar:
- Operador módulo (mod) - muito usado em algoritmos
- Funções matemáticas básicas - abs, raizq, quad
- Funções de string - compr, maiusc, minusc
- Interrompa - controle de laços

## Diferenças da Implementação
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
  
