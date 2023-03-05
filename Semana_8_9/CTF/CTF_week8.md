# CTF da semana 8

## Desafio 1
### Tarefas

#### Explorar a aplicação como um utilizador final.

- É possivel aceder a uma página de login, e a uma função para limpar a sessão.

#### Identificar na aula teórica sobre ataques web uma vulnerabilidade que permite fazer bypass ao login sem conhecer as credenciais

- Utilizando SQL injection, é possivel fazer bypass ao login sem conhecer as credenciais.

#### Analisar o código fonte e tentar identificar se existe alguma das vulnerabilidades elencadas anteriormente.

- É possivel observar que é utilizado nos argumentos da query, o input username e a password, sem qualquer filtração.

#### Identificar a linha onde o código está vulnerável e encontrar uma forma de explorar essa vulnerabilidade.

- Na linha 40, é possivel observar que não existe qualquer filtração do input, e que o que é passado como username e password vai diretamente para a query.

```
$query = "SELECT username FROM user WHERE username = '".$username."' AND password = '".$password."'";
```

 - Usando o username admin e comentando o resto da linha com os carcteres "--" para não utilizar a password, é possível fazer login como admin.

---

##  Código final para obter a flag :
```
Login: admin' --
Password: -
```

---


## Desafio 2
### Tarefas

#### Que funcionalidades é que estão acessiveis a um utilizador sem este estar autenticado?

- É possivel aceder a uma página de fazer login, e a uma página do estado da rede que faz ping a um host definido no input.

#### Das funcionalidade que identificaste e do feedback que tiveste da sua utilização, pensa como é que estas podem estar implementatadas no servidor. Será que estão a utilizar algum utilitário linux?

- A funcionalidade do estado da rede usa um comando linux, o comando ping.

#### Se sim, que vulnerabilidades podem estar presentes na chamada deste utilitário?

- Se a filtragem do input não for feita corretamente, é possível fazer command injection.

#### Verifica se existe alguma vulnerabilidade nesta funcionalidade.

- É possivel fazer command injection, usando entre comandos o caracter ; para separa-los.


##  Comando final para obter a flag :

```
; cat /flag.txt
```