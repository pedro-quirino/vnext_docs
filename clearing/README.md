### Conciliação de bandeira
#### Objetivo
O processo de conciliação visa tirar a complexidade de integrações com bandeiras e adquirentes,
uniformizando o processo e garantindo um fluxo único de informações. 

---
#### Descrição do processo
Diariamente a conciliação de cada bandeira será processada, tendo como base as informações que
passaram pelo autorizador, e o seu resultado disponibilizado para os parceiros de forma centralizada e
padrão.

#### Bandeiras disponíveis:


| BRAND      | MODEL/PARTNER              |    STATUS   |
|------------|----------------------------|:-----------:|
| MASTERCARD | NATIONAL AND INTERNATIONAL |  Validation |
| VISA       | NATIONAL AND INTERNATIONAL |  Validation |
| ELO        | NATIONAL                   |  Available  |
| ELO        | INTERNATIONAL - DISCOVER   |  Available  |
| ELO        | WITHDRAWAL TECBAN NETWORK  | Unavailable |

---
### Integração com emissores
#### Disponibilização da informação

As informações serão disponibilizadas diariamente, seguindo a janela padrão da bandeira. A informação
será disponibilizada no formado json através de estrutura combinada com cada emissor. 

#### Detalhes da informação

As informações para conciliação são disponibilizadas segundo tabela que segue. As informações de
possuem dois agrupamentos, sendo o agrupamento MOVIMENTACAO referentes a operação transacionada 
(uma informação por evento autorizado) e o agrupamento CONCILIACAO referente ao evento que está
sendo conciliado.
Como exemplo, uma compra parcelada em 2x representa uma MOVIMENTACAO, e cada parcela
conciliada representa uma CONCILIACAO. 

