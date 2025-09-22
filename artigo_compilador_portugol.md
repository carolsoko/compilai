### COMPILAÍ: UM COMPILADOR WEB DE PORTUGOL COMPATÍVEL COM VISUALG

Autores
- Nome Sobrenome 1 (Instituição 1, Departamento, Cidade, País, email@exemplo.com)
- Nome Sobrenome 2 (Instituição 2, Departamento, Cidade, País, email@exemplo.com)

Resumo
Este artigo apresenta o Compilaí, um compilador/interpretador Web de Portugol com foco em compatibilidade com a sintaxe do VisuALG e uso educacional. O sistema roda integralmente no navegador, possui editor moderno, execução imediata, depuração e ampla cobertura de construções da linguagem, incluindo tipos, estruturas de controle, funções, procedimentos, arrays 1-based e biblioteca de funções matemáticas e de strings. Descrevemos a fundamentação teórica (interpretação, parsing e conversão para JavaScript), a metodologia de desenvolvimento e avaliação, a evolução por versões (V1, V2 e V3.2), resultados e limitações, e concluímos com perspectivas de trabalho futuro.

Palavras‑chave: Portugol; compiladores; VisuALG; ensino de programação; PWA; Web.

1 Introdução
Portugol é uma notação algorítmica em língua portuguesa amplamente utilizada no ensino introdutório de programação no Brasil. Ferramentas como o VisuALG consolidaram uma sintaxe e um conjunto de recursos que facilitam a transição do raciocínio algorítmico para linguagens imperativas. Entretanto, a dependência de instalações locais e a heterogeneidade de ambientes podem dificultar a adoção em contextos remotos e dispositivos variados. O Compilaí aborda esse problema ao oferecer um compilador/interpretador de Portugol totalmente baseado em Web, com alto grau de compatibilidade com o VisuALG, interface moderna, execução isolada e operação offline via PWA.

Os objetivos do projeto são: (i) prover uma experiência de ensino e aprendizagem acessível em qualquer navegador moderno; (ii) manter compatibilidade com a sintaxe e as construções do VisuALG; (iii) oferecer mecanismos de depuração e mensagens de erro em português; e (iv) evoluir iterativamente a biblioteca padrão e o suporte a estruturas, preservando a simplicidade para iniciantes.

2 Fundamentação teórica
O Compilaí é implementado como uma aplicação Web de página única que combina um editor de código, um motor de parsing e execução, e um subsistema de conversão Portugol → JavaScript. A base conceitual envolve três pilares: (a) análise sintática recursiva; (b) representação intermediária e avaliação; e (c) mapeamento de construções de Portugol para primitivas do ambiente JavaScript.

- Parsing recursivo: Um parser recursivo‑descendente constrói, a partir do código‑fonte, uma estrutura sintática adequada para conversão e/ou interpretação. O tratamento de strings, comentários, separação robusta de argumentos e tokenização de acessos a arrays e chamadas são aspectos críticos. O suporte a arrays 1‑based exige cuidados no reconhecimento e na normalização de índices.
- Conversão para JavaScript: O conversor `convertVisualGToJS` mapeia operadores lógicos (`nao`, `e`, `ou`), relacionais e aritméticos, suporta `mod`, reconhece `pi` como constante e preserva literais. A conversão de acessos a arrays 1D/2D aplica a mudança de base (1‑based → 0‑based) no código gerado, mantendo para o usuário o modelo mental do VisuALG.
- Avaliação de expressões: O avaliador `evalExpression` reconhece literais, nomes, constantes e chamadas de função. Na V3, foram adicionadas funções matemáticas (`exp`, `ln`, `log`, `sin`, `cos`, `tan`) e a constante `pi`, com mapeamento para `Math.*`. Chamadas aninhadas e chamadas de funções definidas pelo usuário em expressões são suportadas com parsing seguro de argumentos.

Do ponto de vista de arquitetura de compiladores, o sistema posiciona‑se entre um interpretador e um compilador de etapa única: realiza parsing e tradução imediata para um subset seguro de JavaScript, que é então executado em um ambiente isolado do navegador. Essa abordagem combina portabilidade com feedback rápido, essencial para cenários educacionais.

3 Metodologia
A evolução do projeto seguiu ciclos incrementais guiados por compatibilidade e priorização didática. Os passos metodológicos foram:

1) Definição do escopo de compatibilidade: alinhar a sintaxe e as construções essenciais do VisuALG (declarações, estruturas de controle, funções/procedimentos, entrada/saída, arrays 1D/2D com indexação 1‑based).
2) Implementação do núcleo: parser recursivo, conversor Portugol → JS, ambiente de execução isolado, tratamento de erros com mensagens em português e sistema de debug (AST, passos de execução, avaliação de expressões).
3) Expansão da biblioteca nativa: priorização de operador `mod`, funções matemáticas e de strings mais usadas (V2) e, posteriormente, ampliação de funções matemáticas e constante `pi` (V3.2).
4) UX e acessibilidade: interface moderna com editor Monaco, layout responsivo, botões de controle, console de saída e indicadores de compatibilidade. Empacotamento PWA via `manifest.json` para operação offline.
5) Avaliação contínua: curadoria de programas de teste (ex.: fatorial com vetor), validação manual e por suíte de casos focados em parsing, indexação 1‑based e correção semântica de operadores/funções.

4 Compilaí: arquitetura e implementação
- Front‑end: HTML5, Tailwind CSS e fontes web asseguram responsividade e legibilidade. O editor Monaco oferece realce e usabilidade adequados ao contexto educacional.
- Motor de linguagem: Implementado em JavaScript ES6+, com parser recursivo, conversor e executor. O sistema preserva escopo local em funções, permite procedimentos acessarem escopo global quando necessário e isola execuções para evitar efeitos colaterais.
- Compatibilidade com VisuALG: Sintaxe de declarações, estruturas de controle (`se/senao`, `repita/ate`, `enquanto/faca`, `para`, `escolha/caso/outrocaso`), funções/procedimentos, operadores (`=`, `<>`, `<`, `>`, `<=`, `>=`, `nao`, `e`, `ou`), E/S (`leia`, `escreva`, `escreval`), arrays 1D e 2D com indexação 1‑based e verificação de limites.
- Biblioteca nativa: V2 adicionou `mod`, `abs`, `raizq`, `quad`, `compr`, `maiusc`, `minusc` e `interrompa`; V3.2 ampliou `exp`, `ln`, `log`, `sin`, `cos`, `tan` e `pi`, além de suportar chamadas aninhadas e funções do usuário em expressões.

5 Resultados
Foram conduzidos testes funcionais com programas didáticos, incluindo a implementação de fatorial com vetor, leitura interativa e impressão formatada. Os resultados indicam:

- Compatibilidade elevada com a sintaxe e a semântica do VisuALG nas construções cobertas. A documentação indica valor‑alvo de compatibilidade de 99,17% para a versão 3.2.
- Execução estável no navegador, inclusive offline via PWA, com mensagens de erro em português e logs de debug que auxiliam no entendimento da execução.
- Conversão correta da indexação 1‑based para 0‑based, com checagem de limites, preservando a expectativa do usuário.
- Biblioteca nativa suficiente para a maioria dos exercícios iniciais de algoritmos, com destaque para operadores essenciais e funções matemáticas/strings mais frequentes.

Limitações concentram‑se em recursos avançados e de ecossistema, como operações de arquivos, persistência entre execuções, funções adicionais de conversão de tipos e utilitários (por exemplo, `timer`, `aleatorio`) quando não cobertos pela versão corrente. Funções trigonométricas operam em radianos, demandando conversão quando necessário.

6 Conclusão
O Compilaí demonstra que é viável oferecer um ambiente de programação educacional completo, compatível com o VisuALG, executando integralmente no navegador com experiência moderna e sem instalação. A arquitetura baseada em parsing recursivo e conversão imediata para JavaScript provê portabilidade, desempenho suficiente e depuração acessível. Como trabalhos futuros, destacam‑se: (i) ampliação da biblioteca nativa (strings avançadas, conversões e utilitários); (ii) suporte a I/O de arquivos e persistência opcional; (iii) expansão de exemplos e testes automatizados; e (iv) melhorias de usabilidade no editor (realce específico de Portugol, autocompletar contextual e dicas semânticas).

Referências
[1] PORTUGOL MODERNIZADO. README.md. 2025.
[2] PORTUGOL MODERNIZADO. Documentação Versão 1 (documentacaoV1.md). 2025.
[3] PORTUGOL MODERNIZADO. Documentação Versão 2 (documentacaoV2.md). 2025.
[4] PORTUGOL MODERNIZADO. Documentação Versão 3 (documentacaoV3.md). 2025.
[5] ECMA INTERNATIONAL. ECMAScript Language Specification. 2023.

