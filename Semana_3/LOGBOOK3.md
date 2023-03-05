
# Trabalho realizado na Semana #3

## Identificação

- Na aplicação **Adobe Acrobat Reader para Android**, até à versão 11.1.3, a restrição para *JavaScript* era insuficiente. 

- Os atacantes podem aproveitar-se desta vulnerabilidade para executar pedaços de código arbitrários.

- Este *exploit* pode resultar num comprometimento dos dados pessoais do utilizador que estejam guardados no seu dispositivo.

## Catalogação

- O *reporting* desta vulnerabilidade foi no dia 13 de abril de 2014, por Yorick Koster. 

- Yorick Koster é co-fundador da empresa Securify, uma empresa de focada em segurança de software.

- O nível de gravidade atribuido pelo *Common Vulnerabity Scoring System* (CVSS) é 9.3 - HIGH.

## Exploit

- Este *exploit* é do tipo **local**, ou seja, esta vulnerabilidade permite ao atacante obter root privileges no dispositivo alvo.

- Este tipo de acesso permite ao atacante aceder a ficheiros guardados tanto na Aplicação como no próprio dispositivo.

- Um atacante pode criar um ficheiro *PDF* contendo código *JavaScript* malicioso. Este corre quando o utilizador interage com o ficheiro através da *app*.

- O uso de código *JavaScript* permite ao atacante ter acesso aos *Reflection APIs* herdados do *Object*. Estes, por sua vez, podem ser usados para correr código *Java*. 
 
## Ataques

- Até à data, não foram verificados ataques usando este *exploit*.

- O identificador verificou este problema na versão 11.1.3 da aplicação para Android.

- Como a *app* fez uma atualização de segurança no dia seguinte à identificação desta vulnerabilidade, a maior parte dos utilizadores ficou protegida da mesma.

- Encontramos um website de *ethical hackers* que explica como realizar um ataque semelhante: https://www.hackeracademy.org/how-to-hack-android-with-a-pdf-file-adobe-reader-exploit/

