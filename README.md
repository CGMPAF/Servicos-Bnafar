# <img src="http://www.saude.gov.br/images/img2/logo-base-nacional.png" height="180">
# Serviços BNAFAR
Serviços da Base Nacional de Dados de Ações e Serviços da Assistência Farmacêutica - BNAFAR
## Nova versão REST
Este projeto é o repositório dos serviços BNAFAR desenvolvidos em REST. Esses serviços estão sendo desenvolvidos pelo Datasus para que os municipios e estados possam transmistir os dados para a BNAFAR, sendo uma opção em relação a primeira versão do [web service SOAP](https://github.com/wsbndaf/Webservice) disponibilizado em 2017.
## Desenvolvimento
O desenvolvimento dos serviços BNAFAR está seguindo as seguintes etapas:
- [x] Elaboração e homologação dos artefatos
- [ ] Desenvolvimento e homologação da API
- [ ] Disponibilização em ambiente de produção

O Datasus estará atuando em todas as etapas acima.
A primeira e segunda etapa são de responsabilidade dos seguintes entes:
1. [Departamento de Assistência Farmacêutica e Insumos Estratégicos do Ministério da Saúde (DAF/SCTIE/MS)](http://www.saude.gov.br/assistencia-farmaceutica)
2. Secretarias Estaduais de Saúde:
    - Minas Gerais
    - Paraná
    - São Paulo
6. Secretarias Municipais de Saúde:
    - Aquiraz/CE
    - Barão de Cocais/MG
    - Blumenau/SC
    - Campinas/SP
    - Fortaleza/CE
    - Goianésia/GO
    - Jequié/BA
    - Rio Branco/AC
    - Ubiratã/PR
    - Vitória/ES
## Cronograma
A perspectiva do Datasus é disponibilizar os serviços em ambiente de produção no primeiro trimestre de 2020. 
Até lá, toda a documentação dos serviços será disponibilizada aqui no GitHub. 
## SOAP x REST
Veja as principais diferenças entre as versões [SOAP](https://github.com/wsbndaf/Webservice) e REST dos serviços da BNAFAR:

Característica | SOAP | REST
-------------- | ---- | ----
Formato arquivos | XML | JSON
Documentação | Manual de integração | Manual de integração + Swagger
Autenticação | Basic Authentication | OAuth 2
#### Consultas
O novo web service em REST contará com um novo serviço especifico para consultas, com várias informações a mais sobre os envios e o status de processamento e de inconsistências. Também será possível obter as relações de protocolos enviados por período de data e por tipo de assunto (ex: entradas, dispensação).
#### Registros
Os registros das operações poderão conter vários produtos. Na versão SOAP, caso o cliente informe a entrada de uma nota fiscal é necessário enviar dezenas de registros, um especifico para cada produto ou lote. Com o REST, cada registro terá um cabeçalho com os dados gerais da operação (entrada/saída/dispensação/estoque) e poderá conter todos os produtos da respectiva ação. Assim, o cliente poderá informar apenas um registro com todos os produtos vinculados a ação.
#### CPF
Na versão REST será possível identificar os pacientes pelo CPF, e não somente pelo CNS como ocorre no SOAP.
#### Identificação dos produtos
Todos os produtos deverão ser informados seguindo o padrão da menor unidade de fornecimento, que é o padrão adotado pelos sistemas de logística. Na versão SOAP, as SES e SMS devem adequar o envio dos seus dados para 14 produtos que possuem unidade de fornecimento diferenciado no Ministério da Saúde (ex: o Levonorgestrel + etinilestradio na versão SOAP deve ser informado utilizando a unidade de fornecimento “1 cartela com 30 comprimidos”. No REST, este deverá ser informado utilizando a menor unidade de fornecimento, ou seja, “comprimido”).
#### Distribuidor de medicamento 
O distribuidor de medicamento (campo obrigatório para as entradas) poderá ser identificado também pelo CNES, e não mais somente pelo CNPJ. O CNES poderá ser utilizado quando ocorrer distribuições entre estabelecimentos de saúde.
#### Médico prescritor
O médico prescritor dos medicamentos do Componente Especializado da Assistência Farmacêutica (CEAF) também poderá ser identificado pelo CNS ou CPF, e não mais apenas pelo CRM.
#### Retificação
Os registros a serem alterados (retificados) não ganharão um novo código de registro interno no web service. Atualmente no SOAP, sempre que um registro é alterado (retificado) o mesmo é inativado e é gerado um novo código de registro. No modelo REST, o registro original será atualizado e não será gerado um novo código de registro.
## Documentação
Os clientes que irão integrar com os serviços contarão com a seguinte documentação:
#### Swagger
#### Manual de integração
## Maiores informações sobre a BNAFAR
:link: Acesse o sítio eletrônico da BNAFAR no [Portal do Ministério da Saúde](http://www.saude.gov.br/assistencia-farmaceutica/base-nacional-de-dados) e obtenha todas as informações sobre a Base.
## Contato
:envelope: ws.daf@saude.gov.br

:telephone_receiver: 136
