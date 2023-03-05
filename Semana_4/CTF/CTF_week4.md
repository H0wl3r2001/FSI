# CTF da semana 4

## CVE exploitation

### Objetivo: Fazer login como administrador

- Explorou-se um serviço de wordpress que na sua conceção teria uma vulnerabilidade que me permetiria dar *login* como administrador. Após cuidada inspeção do site (http://ctf-fsi.fe.up.pt:5001), verificou-se que a versão de um dos plugins (5.4.3 do *booster for WooCommerce plugin*) era vulnerável, quando cruzada na base de dados de CVE's (https://www.exploit-db.com/).
- Após pesquisa desse plugin na tal base de dados, encontrou-se um script em python que abusava do sistema de requerimento de novas passwords. Ou seja, quando um utilizador dizia que queria recuperar a password do utilizador "admin", poderia pôr um email à escolha e depois era automaticamente autenticado como esse mesmo utilizador, sem precisar de password.