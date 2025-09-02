# Portugol Modernizado – Documentação Versão 3 (compiladorPortugolV3.html)

## Visão Geral
A Versão 3 amplia a biblioteca matemática e melhora o avaliador de expressões, trazendo suporte a:
- Funções matemáticas novas: `exp(x)`, `ln(x)`, `log(x)`, `sin(x)`, `cos(x)`, `tan(x)`
- Constante: `pi`
- Chamadas aninhadas de funções (ex.: `ln(exp(1))`)
- Avaliação direta de funções definidas pelo usuário em expressões (ex.: `fat(j)`)

Mantém compatibilidade com a sintaxe do VisualG e as funcionalidades já existentes nas versões anteriores (arrays 1-based, `mod`, `escreva(l)`, estruturas de controle, funções e procedimentos, etc.).

## Novidades da Versão 3
- `exp(x)`: exponencial (base e), mapeada para `Math.exp(x)`
- `ln(x)`: logaritmo natural, `Math.log(x)`
- `log(x)`: logaritmo base 10, `Math.log10(x)` quando disponível; fallback `Math.log(x)/Math.LN10`
- `sin(x)`, `cos(x)`, `tan(x)`: trigonométricas em radianos (use `pi` para converter)
- `pi`: constante π (`Math.PI`)
- Avaliador aprimorado:
  - Suporta chamadas aninhadas de built-ins (ex.: `ln(exp(1))`)
  - Avalia chamadas de funções definidas pelo usuário diretamente em expressões (ex.: `fat(x-1)`) 

## Exemplo de Uso
```portugol
// Função recursiva de fatorial e uso de recursos da V3
inteiro n, i
inteiro fatorial[10]
funcao fat(x): inteiro
    se x = 0 entao
        retorna 1
    senao
        retorna x * fat(x-1)
    fimse
fimfuncao

escreval("exp(1) = ", exp(1))
escreval("ln(exp(1)) = ", ln(exp(1)))
escreval("log(100) = ", log(100))
escreval("pi = ", pi)
escreval("sin(pi/2) = ", sin(pi/2))

escreval("Digite o tamanho do vetor (max 10): ")
leia(n)

procedimento preencherFatorial(tam)
    inteiro j
    j <- 1
    repita
        fatorial[j] <- fat(j)
        j <- j + 1
    ate (j > tam)
fimprocedimento

preencherFatorial(n)

i <- 1
repita
    escreval("fatorial[", i, "] = ", fatorial[i])
    i <- i + 1
ate (i > n)
```

Dica: funções trigonométricas usam radianos. Por exemplo, `sin(pi/2)` ≈ 1.

## Notas de Implementação
- Avaliador (`evalExpression`):
  - Trata literais de string e números diretamente
  - Reconhece `pi` como constante
  - Avalia built-ins suportados (`abs`, `raizq`, `quad`, `compr`, `maiusc`, `minusc`, `exp`, `ln`, `log`, `sin`, `cos`, `tan`)
  - Avalia chamadas de funções do usuário quando a expressão inteira é uma chamada (`nome(args)`), com parsing seguro dos argumentos (`splitTopLevelArgs`)
- Conversor (`convertVisualGToJS`):
  - Preserva strings
  - Converte `nao`, `e`, `ou`, operadores relacionais e `mod`
  - Tokeniza acessos a arrays (1D e 2D) e chamadas antes de converter variáveis
  - Substitui `pi` por token de constante
- Arrays 1-based: acessos e atribuições convertem para 0-based internamente
- Operador `mod`: suportado
- `interrompa`: suportado em laços

## Limitações e Observações
- Trigonométricas em radianos (converta graus para radianos se necessário)
- `log(x)` é base 10; para natural, use `ln(x)`
- Para evitar ambiguidade em parsing, prefira sempre fechar corretamente parênteses e usar vírgulas para separar argumentos

## Mudanças vs. Versão 2
- Adição de 6 funções matemáticas + constante `pi`
- Suporte a chamadas aninhadas de built-ins
- Suporte a chamadas diretas de funções do usuário dentro de expressões
- Ajustes de robustez no parsing de `caso` e chamadas genéricas

## Como Testar
1. Abra `compiladorPortugolV3.html` no navegador
2. Execute o código de exemplo (botão “Executar”) e verifique a saída
3. Ative “Debug” para inspecionar a AST e as expressões convertidas quando necessário

## Arquivo Relacionado
- Implementação: `compiladorPortugolV3.html`
- Documentações anteriores: `documentacaoV1.md`, `documentacaoV2.md`

        