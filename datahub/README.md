Buscando concentrar o fluxo de encaminhamento de mensagens e comunicação 
criptografada com os emissores, foi concebida a API Webhooks. Inicialmente, 
serão fornecidos aos emissores, dados vindos do serviço Conductor DataHub, 
que tem como função principal verificar e publicar alterações ocorridas em 
bases de dados, utilizando do serviço do SQL Server Change Data Capture.

#### Api webhook

Para receber as mensagens providas pelo DataHub, é necessário informar quais 
eventos devem ser enviados, além dos dados dos recursos que devem receber os 
respectivos tipos de dados de cada evento. Nessas informações devem constar o 
tipo de evento, a URL do webhook, os cabeçalhos necessários para autenticação; 
o restante do tratamento é feito pela Conductor.

Para conhecer a documentação da Api, [clique aqui](https://documenter.getpostman.com/view/6944804/SW15xbpj)