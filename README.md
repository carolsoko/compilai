# Portugol Modernizado
Repositório do Projeto Portugol Modernizado

Contém as versões dos compiladores criados no projeto

# Versão 3.2 - arquivo compilai.html - lista de funcionalidades adicionadas em relação à versão 2.0:

Amplia a biblioteca matemática e melhora o avaliador de expressões, trazendo suporte a:

Funções matemáticas novas: exp(x), ln(x), log(x), sin(x), cos(x), tan(x)
Constante: pi
Chamadas aninhadas de funções, ou seja, recursividade (ex.: ln(exp(1)))
Avaliação direta de funções definidas pelo usuário em expressões (ex.: fat(j))
Mantém compatibilidade com a sintaxe do VisualG e as funcionalidades já existentes nas versões anteriores (arrays 1-based, mod, escreva(l), estruturas de controle, funções e procedimentos, etc.).

- **exp(x)** exponencial (base e), mapeada para Math.exp(x)
- **ln(x)**  logaritmo natural, Math.log(x)
- **log(x)**  logaritmo base 10, Math.log10(x) quando disponível; fallback Math.log(x)/Math.LN10
- **sin(x), cos(x), tan(x)**  trigonométricas em radianos (use pi para converter)
- **pi**  constante π (Math.PI)
- **Suporta chamadas aninhadas de built-ins**  (ex.: ln(exp(1)))
- **Avalia chamadas de funções definidas pelo usuário diretamente em expressões**  (ex.: fat(x-1))


# Versão 2.0 - arquivo compiladorPortugolV2.html - lista de funcionalidades adicionadas em relação à versão 1.0:

- **Operador MOD** para resto de divisão (x mod 3)
- **Função ABS** para valor absoluto (abs(x))
- **Função RAIZQ** para raiz quadrada (raizq(x))
- **Função QUAD** para elevar ao quadrado (quad(x))
- **Função COMPR** para comprimento de string (compr(texto))
- **Função MAIUSC** para converter maiúscula (maiusc(texto))
- **Função MINUSC** para converter minúscula (minusc(texto))
- **Comando INTERROMPA** para sair de laços


# Versão 1.0 - arquivo compiladorPortugolV1.html - lista de funcionalidades implementadas:

Um compilador/interpretador completo de Portugol (VisualG) que funciona diretamente no navegador.

## Características

- **100% compatível** com a sintaxe VisualG
- **Interface amigável** com editor de código e console de saída
- **Execução em tempo real** no navegador (sem servidor)
- **Arrays 1-based** seguindo o padrão VisualG - **Falta verificar se as matrizes estão funcionando corretamente**
- **Funções e procedimentos** com escopo adequado
- **Sistema de debug** integrado

## Sintaxe Suportada

### Tipos de Dados
```portugol
inteiro x, y
real nota
caractere nome
logico ativo
inteiro vetor[10]
inteiro matriz[3][4]
```

### Estruturas de Controle
```portugol
se (x > 0) entao
    escreval("Positivo")
fimse

repita
    x <- x + 1
ate (x > 10)

para i de 1 ate 5 faca
    escreval(i)
fimpara
```

### Funções e Procedimentos
```portugol
funcao fatorial(n): inteiro
    se n = 0 entao
        retorna 1
    senao
        retorna n * fatorial(n-1)
    fimse
fimfuncao
```

## Como Usar

1. **Online:** Acesse o arquivo HTML no navegador
2. **Offline:** Baixe o arquivo `compiladorPortugolV1.html` e abra localmente
3. **Edite o código** na área à esquerda
4. **Clique em "Executar"** para rodar o programa
5. **Use "Debug"** para ver detalhes da execução

## Exemplo Funcional

O interpretador inclui um exemplo de cálculo de fatorial que demonstra todas as funcionalidades principais.

## Tecnologias

- HTML5, CSS3, JavaScript ES6+
- Parser recursivo personalizado
- Ambiente de execução isolado
- Sistema de conversão Portugol → JavaScript

## Documentação Completa

Consulte `documentacaoV1.md` para detalhes técnicos completos e lista de todas as funcionalidades implementadas.
