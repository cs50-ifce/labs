# Olá

## Listar Arquivos

(Esta é uma tradução do laboratório 'hello' do curso CS50. A versão original pode ser acessada [clicando aqui](http://lab.cs50.io/cs50/labs/2020/x/hello).)

Olá, mundo! Vamos começar: No *editor de texto*, tem o primeiro programa já escrito em C em um arquivo chamado `ola.c`.

Clique no ícone de pasta e você verá que o arquivo `ola.c` é o único arquivo até o momento. Clique no ícone da pasta novamente para ocultar os arquivo.

Agora, na *janela de terminal*, imediatamente após o símbolo de sifrão (`$`), também conhecido como *prompt*, digite **exatamente**, em letras minúsculas, o comando abaixo e pressione a tecla Enter:
```
ls
```

Você deveria vê exatamente `ola.c`? Isto é por que você está, simplesmente, listando os arquivo na mesma pasta, mas desta vez usando a interface de linha de comando (do inglês, *command-line interface, CLI*) usando apenas seu teclado em vez de uma interface gráfica de usuário (*do inglês, Graphical User Interface, GUI*) representado pelo ícone da pasta. Em particular, você **executou** um comando chamado `ls`, que é uma abreviatura para "*list*" (listar, em inglês). Este comando é tão usado que os programadores que o escreveram preferiram chamar de `ls` para economizar digitação. ]faz sentido?

Daqui em diante, executar um comando significa digitar o comando na janela de terminal e apertar Enter. Comandos são "*case-sensitive*", isto é, diferenciam letras MAIÚSCULAS e minúsculas. Então não confunda.

{% next %}

## Compilando Programas

Agora, antes de executarmos um programa, nós precisamos **compilar** o que é feito usando um **compilador** (por exemplo, `clang` ou `gcc`) que traduz o **código-fonte** para **linguagem de máquina** (isto é, zeros e uns). Execute o comando exatamente como abaixo:
```
clang ola.c
```

E então execute o comando `ls`novamente:

```
ls
```

Desta vez, você deveria ver o arquivo `a.out` além do `ola.c` (Você pode ver graficamente clicando no ícone da pasta novamente). O que ocorreu foi que o comando `clang` traduziu o código-fonte existente no arquivo `hello.c` em código de máquina (ou em **código assembly**, mas falaremos disto depois) e salvou o conteúdo no arquivo `a.out`.

Agora, execute o programa com o comando abaixo:

```
./a.out
```

"Olá, mundo!", de fato!

{% next %}

## Nomeando Programas

Agora, `a.out` não é o nome mais amigável para um programa. Vamos compilar `ola.c` novamente, desta vez salvando o código da máquina em um arquivo chamado, mais apropriadamente, `ola`. Execute o abaixo.

```
clang -o ola ola.c
```

Tome cuidado para não esquecer nenhum desses espaços! Em seguida, execute este novamente:

```
ls
```

Agora você deve ver não apenas `ola.c` (e `a.out` de antes), mas também `ola` listado também? Isso porque `-o` é um **argumento de linha de comando**, às vezes conhecido como **flag** (**bandeira**) ou **switch** (**chave**, neste caso), que indica ao `clang` para saída (daí o `o` de *output* que significa saída em português) um arquivo chamado `ola`. Execute o abaixo para experimentar o programa recém-nomeado.

```
./ola
```

"Olá, mundo!", de novo!

{% next %}

## Tornando as coisas mais fáceis
 
Recall that we can automate the process of executing `clang`, letting `make` figure out how to do so for us, thereby saving us some keystrokes. Execute the below to compile this program one last time.
Podemos automatizar o processo de execução do `clang`, deixando o comando `make` descobrir como fazer isso por nós, economizando digitação (lembre-se, programadores são seres preguiçosos que sempre procuram economizar trabalho, inclusive o trabalho de digitar). Execute o abaixo para compilar este programa uma última vez.

```
make ola
```

Você deve ver que o `make` executa `clang` com ainda mais argumentos de linha de comando para você! Falaremos sobre isso também, outra hora!

Agora execute o próprio programa uma última vez executando o abaixo.

```
./ola
```

Bum!

## Solicitando informações ao usuário

Basta dizer que, não importa como você compile ou execute este programa, ele sempre imprimirá 'olá, mundo'. Vamos personalizá-lo um pouco, como fizemos na aula.

Modifique este programa de forma que primeiro solicite o nome do usuário e, em seguida, imprima `ola, fulano`, onde `fulano` é o nome real.

Como antes, certifique-se de compilar seu programa com:

```
make ola
```

E não deixe de executar seu programa, testando-o algumas vezes com entradas diferentes, com:

```
./ola
```

### Solução do professor

Tente a solução do professor para este problema, execute

<pre>
./ola
</pre>

com [esta máquina virtual](https://bit.ly/2BDU78M).

### Passo a passo

{% video https://www.youtube.com/watch?v=wSk1KSDUEYA %}
Em inglês, com legendas. Em breve teremos vídeo em português.

### Digas

#### Não lembra como solicitar o nome do usuário?

Lembre de usar `get_string` como segue, armazenando o **valor de retorno** em uma variável chamada `nome` do tipo `string`.

```c
string nome = get_string("Qual seu nome? ");
```

#### Não lembra como exibir uma string?

Não se lembra de como associar (ou seja, concatenar) o nome do usuário com uma saudação? Lembre-se de que você pode usar o `printf` não apenas para imprimir, mas para formatar uma string (daí o `f` em `printf`), como abaixo, em que  `nome` é uma `string`.


```c
printf("Ola, %s\n", nome);
```

#### Obteve um erro "undeclared identifier"?

Apareceu uma mensagem de erro como abaixo?

```
error: use of undeclared identifier 'string'; did you mean 'stdin'?
```

Lembre-se de que, para usar `get_string`, você precisa incluir a biblioteca `cs50.h` (onde `get_string` é **declarado**) no início do seu arquivo, como em:

```c
#include <cs50.h>
```

### Como testar seu código

Execute o abaixo para avaliar a correção do seu código usando `check50`, mas certifique-se de compilar e testar você mesmo!

```
check50 ifce-lab-prog/problemas/2020/1/ola
```

Execute o comando `style50` como abaixo para avaliar o estilo do seu código.

```
style50 ola.c
```

{% next %}

## Envie sua resposta

Execute o procedimento abaixo, fazendo login com seu **nome de usuário** e senha do **GitHub** quando solicitado. Por segurança, você verá asteriscos (`*`) em vez dos caracteres reais em sua senha.

```
submit50 ifce-lab-prog/problemas/2020/1/ola
```