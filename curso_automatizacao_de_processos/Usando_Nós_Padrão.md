# Utilizando nós padrão no n8n

Neste curso, foram apresentados os principais nós utilizados na construção de workflows no n8n e como cada um deles participa de uma automação, desde o recebimento dos dados até o envio das informações para outros sistemas.

## 1. Arquitetura básica de um workflow

Um workflow pode ser entendido como um processo com começo, meio e fim. Ele recebe dados, realiza operações e encaminha os resultados para outros sistemas ou aplicações.

De maneira geral, temos três partes:

- **Trigger (gatilho):** inicia o workflow e recebe os dados de entrada.
- **Processamento:** manipula os dados, realiza consultas e define condições para o fluxo.
- **Action (ação):** envia informações para outro sistema ou executa alguma ação externa.

Um workflow pode receber dados de um sistema A, processá-los e enviar o resultado para um sistema B. Embora o nó de ação geralmente apareça no final, ele também pode estar no meio do fluxo, caso seja necessário continuar o processamento depois dele.

## 2. Nós apresentados no curso

### Webhook

O Webhook é um tipo de trigger que permite iniciar um workflow a partir de uma requisição HTTP. Ele disponibiliza uma URL para que outros sistemas enviem informações ao n8n.

Durante o curso, foi utilizado o site [ReqBin](https://reqbin.com/) para simular o envio de dados ao Webhook.

Alguns conceitos importantes:

- **Test URL e Production URL:** o n8n disponibiliza URLs para testar o Webhook e para utilizá-lo em produção.
- **GET:** geralmente utilizado para enviar parâmetros pela URL, como parâmetros de consulta (*query parameters*).
- **POST:** geralmente utilizado para enviar informações no corpo da requisição (*request body*).
- **PATH:** define o caminho utilizado na URL do Webhook. Pode ser personalizado, mas deve evitar espaços, acentos e caracteres especiais.

A escolha do método HTTP depende do que o sistema que envia os dados espera e da forma como a requisição precisa ser construída.

### HTTP Request

O nó HTTP Request permite fazer requisições a APIs e outros serviços que disponibilizam uma interface HTTP.

No curso, ele foi utilizado para consultar uma API de cotação de moedas.

- **GET:** utilizado para consultar informações de um endpoint e receber os dados retornados pela API.
- **POST:** utilizado para enviar dados a outro sistema por meio de uma requisição HTTP.

O HTTP Request pode atuar como nó de processamento ou como parte de uma ação externa, dependendo da finalidade da requisição e de como o resultado será utilizado no workflow.

É importante consultar a documentação da API antes de configurar o nó, pois ela informa a URL do endpoint, os métodos aceitos, os parâmetros necessários e o formato esperado dos dados.

API utilizada durante a aula: [AwesomeAPI — API de moedas](https://docs.awesomeapi.com.br/api-de-moedas).

### Edit Fields

O nó Edit Fields permite selecionar, criar e modificar campos dos dados que passam pelo workflow.

Ele pode ser utilizado para criar variáveis, organizar informações recebidas de outros nós e preparar os dados para as próximas etapas da automação.

### IF

O nó IF permite criar condições para decidir qual caminho o workflow deve seguir.

A partir de uma condição, os dados podem ser direcionados para caminhos diferentes, de acordo com o resultado da verificação.

### Switch

O nó Switch também permite direcionar os dados por diferentes caminhos, mas é especialmente útil quando existem várias condições ou classificações possíveis.

Enquanto o IF costuma ser utilizado para uma decisão condicional mais simples, o Switch facilita a organização de múltiplas rotas dentro do mesmo workflow.

## 3. Workflow desenvolvido durante as aulas

O workflow construído no curso simulou um processo de recebimento, consulta, tratamento e encaminhamento de informações. Para facilitar o entendimento, as etapas foram associadas a diferentes setores de uma empresa.

### 1. Tecnologia — recebimento dos dados

**Nó:** Webhook (POST)

O fluxo começa com um Webhook configurado para receber uma requisição POST. Utilizando o ReqBin, foi possível simular o envio de informações para a URL de teste do Webhook.

Essa etapa representa o recebimento e o monitoramento de eventos de um sistema, como poderia acontecer em um setor de tecnologia.

### 2. Mercado Financeiro — consulta de informações

**Nó:** HTTP Request (GET)

Em seguida, o workflow realiza uma consulta à AwesomeAPI para obter informações sobre a cotação de moedas.

Essa etapa demonstra como uma automação pode buscar dados externos e utilizá-los nas próximas operações. Um exemplo de aplicação seria consultar cotações ou outras informações financeiras disponibilizadas por uma API.

### 3. Saúde — tratamento e classificação dos dados

**Nós:** Edit Fields, IF e Switch

Depois de receber as informações, o workflow utiliza nós de processamento para transformar os dados, criar campos e avaliar condições.

O Edit Fields permite preparar as informações, enquanto o IF e o Switch definem caminhos diferentes de acordo com as condições estabelecidas.

Essa parte representa uma triagem: os dados são avaliados e classificados para determinar qual ação deve acontecer em cada situação.

O Switch também permite organizar diferentes estados ou classificações, facilitando a criação de regras para encaminhar as informações.

### 4. Indústria — tratamento de erros

Durante a construção do workflow, também foi considerada a possibilidade de ocorrerem erros durante a execução.

A proposta foi simular situações adversas para observar o comportamento da automação e entender como lidar com falhas.

Essa etapa reforça a importância de consultar a documentação dos sistemas envolvidos e observar as respostas retornadas pelas requisições para identificar a origem de um problema e definir como tratá-lo.

### 5. Saída — armazenamento e comunicação

**Nós:** Google Sheets e Gmail

Ao final do processo, foram utilizadas duas possibilidades para encaminhar os resultados:

- **Google Sheets:** permite adicionar informações a uma planilha, mantendo um registro dos dados produzidos pelo workflow para consultas e análises futuras.
- **Gmail:** permite enviar os resultados da automação por e-mail, facilitando a comunicação e a verificação de informações importantes.

Essas integrações mostram como um workflow pode conectar diferentes aplicações para armazenar dados e comunicar resultados sem depender de todas essas etapas serem realizadas manualmente.

## 4. Principais aprendizados

Ao longo do curso, foram explorados os seguintes conceitos:

- Estrutura básica de um workflow, desde o gatilho até as ações.
- Utilização de Webhooks para receber dados por requisições HTTP.
- Diferenças entre requisições GET e POST.
- Consultas a APIs externas utilizando HTTP Request.
- Manipulação de dados com Edit Fields.
- Criação de condições e caminhos alternativos com IF e Switch.
- Integração com Google Sheets e Gmail.

## 5. Registro visual

Abaixo está a imagem final do workflow desenvolvido durante as aulas.

<img width="1447" height="588" alt="image" src="https://github.com/user-attachments/assets/4752644a-3122-4a13-aa08-2fe22e0ca4a2" />

