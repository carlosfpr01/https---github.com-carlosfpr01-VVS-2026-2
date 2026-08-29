# Uso da IA
## Parte 1
### Pergunta
- explique resumidamente o que são ruleset, configLocation, failOnViolation, maxAllowedViolations e violationSeverity.
Não me de exemplos de pom.xml
### Resposta

Resumo rápido
Esses termos controlam como uma validação de qualidade funciona:

- ruleset: conjunto de regras que a ferramenta vai verificar.
- configLocation: onde está a configuração dessas regras.
- failOnViolation: se uma violação deve quebrar a execução/build.
- maxAllowedViolations: quantas violações são permitidas antes de falhar.
- violationSeverity: qual gravidade da violação importa para decidir se deve bloquear.
Em uma frase
Eles definem “quais regras usar”, “onde elas estão”, “quais problemas contam”, “quantos problemas são tolerados” e “se o sistema deve falhar ao encontrar um problema”.

    Em outras palavras: são parâmetros de política de qualidade e controle de bloqueio da validação.
---

## Parte 5

### Pergunta
Após ler as mensagens perguntei o que era os erros relatados

    O que significa os erros a baixo no Target do checkStyles?
    <?xml version="1.0" encoding="UTF-8"?>
    <checkstyle version="9.3">
    <file name="/home/kali/Projects/books/users/src/main/java/dev/rpmhub/web/Users.java">
    <error line="1" severity="error" message="Missing package-info.java file." source="com.puppycrawl.tools.checkstyle.checks.javadoc.JavadocPackageCheck"/>
    <error line="3" column="1" severity="error" message="Javadoc comment is placed in the wrong location." source="com.puppycrawl.tools.checkstyle.checks.javadoc.InvalidJavadocPositionCheck"/>
    </file>
    <file name="/home/kali/Projects/books/users/src/main/resources/application.properties">
    <error line="1" severity="error" message="File does not end with a newline." source="com.puppycrawl.tools.checkstyle.checks.NewlineAtEndOfFileCheck"/>
    </file>
    </checkstyle>

### Resposta
    O que esses erros significam
    1) Missing package-info.java file
    Esse erro quer dizer que a regra de Javadoc do Checkstyle exige um arquivo package-info.java para o pacote da classe.

    Ou seja, no pacote da classe em Users.java, o Checkstyle espera um arquivo como:

    users/src/main/java/dev/rpmhub/web/package-info.java
    Esse arquivo normalmente só contém:

    a declaração do pacote
    um comentário Javadoc do pacote
    2) Javadoc comment is placed in the wrong location
    Isso acontece porque o comentário de licença/topo do arquivo está antes da declaração do pacote.

    Em Java, a ordem correta é:

    comentário opcional
    package
    imports
    classe
    Se a sua file tiver um bloco Javadoc no início antes de package, o Checkstyle considera isso fora do lugar.

    Em outras palavras: o comentário está “na posição errada” em relação à estrutura do arquivo.

    3) File does not end with a newline
    Esse é simples: o arquivo application.properties não termina com uma quebra de linha.

    Isso geralmente é resolvido salvando o arquivo com uma última linha em branco.

    Resumo
    Esses erros não são do Java em si; são regras de estilo/javadoc do Checkstyle:

    falta de documentação do pacote
    comentário no lugar errado
    arquivo de configuração sem newline final
    Se quiser, posso te mostrar exatamente como arrumar o topo de Users.java e criar o package-info.java correto.



## Parte 6
Arrumei o primeiro erro, posterior a isso pedi pra arruma o que tinha me indicado antes

### Pergunta
    Arrume os pontos marcados no arquivo o checkstyle-result
### Resposta
    