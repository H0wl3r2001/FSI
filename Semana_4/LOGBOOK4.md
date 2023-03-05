# Trabalho realizado na Semana 4

## Environment Variable and Set-UID Program Lab

### Tarefa 1

- Corremos as tarefas na SeedLabs virtual box e observámos os valores das várias variáveis de ambiente.
- Conseguimos ver  a execução do export nome_variável="" e do unset NOME_VARIAVEL

### Tarefa 2

- O resultado obtido foi semelhante ao da tarefa 1.
- AS variáveis de ambiente do child process e do parent process são as mesmas, quando as duas versões do
programa são executadas a partir do mesmo terminal.

### Tarefa 3

- Step 1 : Não verificamos qualquer output
- Step 2 : Alterando de NULL para environ conseguimos observar as variáveis de ambiente através do terminal 
- Step 3: A alteração de NULL para environ fez com que o programa conhecesse todas as variáveis de ambiente dos nossos sistemas.
    A variável "_" ( " represents the full pathname used to invoke each command executed and placed in the environment exported to that command") era a única diferente na execução do comando env na shell (/usr/bin/env) para a execução desse comando através do código execve() no programa (./a.out) - obtido por executar diff entre ficheiros de output

### Tarefa 4
- A função system() é executada pelo programa. Retorna um conjunto de variáveis de ambiente que vêm ordenadas de forma diferente do que o que viria na execução do comando env na *shell*. Verificamos, com o auxílio do comando *diff*, que há diferenças presentes. O número de linhas eram iguais, mas as variáveis apareciam em locais diferentes.

### Tarefa 5

Executamos os varios passos e executando ls -l foo o nome do programa apareceu sombreado a vermelho, o que significa que as permissões foram escaladas.
- No Step 3: Conseguiu-se alterar *PATHS*, mesmo sendo um utilizador comum, porque tinha na sua posse um ficheiro de permissões escaladas com o programa que permitiu fazê-lo, alterando o dono e o modo desse mesmo ficheiro. 

- Conseguimos observar alterações nas variávies PATH e na variável que criamos chamada "FSI", mas não conseguimos encontrar a variável LD_LIBRARY_PATH quando realizamos printenv.

- Alterando a variáveç Path o terminal deixou de conseguir encontrar qualquer programa (incluindo a data para apresentar e printenv)

- Sem alterar o PATH, ou seja mantendo o acesso a printenv, pudemos comparar as variáveis alteradas na shell com as impressas no programa foo e verificamos a sua igualdade, embora apareçam em locais diferentes.

### Tarefa 6

- Conseguimos fazer como na tarefa anterior e transformar o programa fornecido num programa SET-UID, aparecendo também sombreado a vermelho.

- É possível utilizar este SET-UID program para correr o nosso código malicioso, em vez de "ls". 

- Experimentámos mudar o comando a ser executado por system() para system("sudo chmod 0000 foo"), o que permitir retirar todas as permissões do executável foo (observável com ls -l foo: "---------- 1 root seed 16768 Nov 12 05:16 foo), sendo que depois ficou impossível executá-lo: ([11/17/21]seed@VM:~/.../Env_var_SETUID$ ./foo
bash: ./foo: Permission denied").

- Não consegui fazer alteração de variáveis de ambiente com o system neste executável tsk6

- Com isto, acreditamos que provavelmente seria possível alterar informações mais importantes do sistema como variáveis de systema e etc., podendo p.e. causar Denial of Services ou ataques mais graves.