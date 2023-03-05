# Trabalho realizado na Semana #5

## Buffer overflow attack Lab

### Tarefa 1

- Executando o código, abriu uma shell
- Na shell da Matilde o backspace não apaga "graficamente" o texto anteriormente escrito mas é apagado em termos de "o que vai correr"

### Tarefa 2

- Executando a *script* pretendida, criou-se um conjunto de 4 ficheiros stack-Lx (x estando entre 1 e 4), com permissões *root*.

### Tarefa 3

#### Na versão stack-L1-dbg
- gdb-peda$ p $ebp
- $1 = (void *) 0xffffca98
- gdb-peda$ p &buffer
- $2 = (char (*)[100]) 0xffffca2c

Buffer está acima na stack em relação ao ebp (Base pointer da stack)

Analisando o output do comando "x/100wx buffer" que mostra 100 palavras do buffer conseguimos ver qual é o endereço de ret somando 4 ao endereço do base stack pointer (no nosso exemplo 0xffffca9c)
O que nos permite calcular o valor do offset em decimal, sendo este o valor do endereço de ret - o endereço do buffer (112 = 108 (ebp-buff) + 4)

#### Na versão stack-L1

- Através da recomendação do professor, utilizamos os valores anteriormente calculados e, para funcionar corretamente descobrimos o endereço atual do buffer com o auxílio de um printf ("printf("buf is at : %p\n", buffer);")

## Tarefas Opcionais

### Tarefa 4 



### Tarefa 5