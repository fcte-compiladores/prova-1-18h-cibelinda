De modo abstrato, o compilador é um programa que converte código de uma
linguagem para outra. Como se fosse uma função do tipo `compilador(str) -> str`.
No caso de compiladores que emitem código de máquina ou bytecode, seria mais
preciso dizer `compilador(str) -> bytes`, mas a idéia básica é a mesma.

De forma geral o processo é dividido em etapas como abaixo

```python
def compilador(x1: str) -> str | bytes:
    x2 = lex(x1:str) -> List[Token]     # análise léxica
    x3 = parse(x2 List[Token]) -> AST   # análise sintática
    x4 = analysis(x3: AST) -> AST  # análise semântica
    x5 = optimize(x4: AST) -> AST   # otimização
    x6 = codegen(x5: AST) -> str | bytes    # geração de código
    return x6
```

Defina brevemente o que cada uma dessas etapas realizam e marque quais seriam os
tipos de entrada e saída de cada uma dessas funções. Explique de forma clara o
que eles representam. Você pode usar exemplos de linguagens e/ou compiladores
conhecidos para ilustrar sua resposta. Salve sua resposta nesse arquivo.

# lex(x1:str) -> List[Token]
A análise léxica recebe o código fonte como uma string e converte em uma lista de tokens, que são as menores unidades significativas do programa (palavras-chave, identificadores, números, símbolos, etc).  
*Exemplo:* Para print 1+2; gera [PRINT, NUMBER(1), PLUS, NUMBER(2), SEMICOLON].
 
# parse(x2:List[Token]) -> AST
A análise sintática recebe a lista de tokens e constrói a Árvore Sintática Abstrata (AST), que representa a estrutura gramatical do programa.  
*Exemplo:* Os tokens acima viram um nó PrintStmt(Binary(Number(1), PLUS, Number(2))).

# analysis(x3:AST) -> AST
A análise semântica verifica regras como tipos, variáveis não declaradas, escopos, etc. Pode anotar a AST com informações extras.  
*Exemplo:* Detecta uso de variáveis não declaradas ou verifica se operações são válidas.

# optimize(x4:AST) -> AST
A otimização transforma a AST para gerar código mais eficiente, sem alterar o resultado do programa.  
*Exemplo:* Simplifica 1 + 2 para 3, remove código morto, etc.

# codegen(x5:AST) -> str|bytes
A geração de código converte a AST em código alvo, como bytecode, assembly ou código de máquina.  
*Exemplo:* No Lox, gera bytecode para a VM; em C, pode gerar assembly.