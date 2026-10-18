# Projeto — Processo Seletivo de RH

Neste projeto, foi desenvolvida uma automação no n8n para auxiliar o processo seletivo de uma empresa. A ideia é utilizar uma planilha com os dados dos candidatos para verificar quem atende aos critérios da vaga e enviar as comunicações correspondentes automaticamente.

## 1. Objetivo da automação

O processo começa com uma planilha do Google Sheets contendo as informações dos candidatos inscritos no processo seletivo.

Quando o período de candidaturas termina, a automação é executada para separar os candidatos em dois grupos:

- **Aprovados para a próxima fase:** recebem um e-mail informando a aprovação.
- **Não aprovados:** têm seus nomes reunidos em uma lista, que é enviada por e-mail ao responsável pelo RH.

Dessa forma, o workflow automatiza a classificação inicial dos candidatos e o envio das comunicações, reduzindo a necessidade de realizar essas tarefas manualmente.

## 2. Critérios de aprovação

Para este projeto, foram definidos dois requisitos que precisam ser atendidos simultaneamente:

- Ter mais de 5 anos de experiência na área.
- Possuir grau de escolaridade superior.

O nó IF é responsável por verificar essas condições e direcionar cada candidato para o caminho correspondente.

## 3. Etapas do workflow

### Schedule Trigger — início da automação

O workflow começa com um nó de agendamento (*Schedule Trigger*), que permite definir o dia e o horário em que a automação será executada.

A proposta é configurar o fluxo para rodar após o encerramento do período de inscrições, quando já for possível avaliar as candidaturas recebidas.

### Get Rows — leitura dos candidatos

O nó do Google Sheets é utilizado para recuperar as linhas da planilha que contém os dados dos candidatos.

Essas informações são encaminhadas para a etapa seguinte, na qual serão avaliadas de acordo com os critérios estabelecidos.

### IF — verificação dos requisitos

O nó IF verifica se cada candidato atende aos dois critérios de aprovação: experiência superior a 5 anos e escolaridade superior.

A partir do resultado, os candidatos são direcionados para caminhos diferentes:

- **Saída verdadeira (True):** candidatos que atendem aos requisitos.
- **Saída falsa (False):** candidatos que não atendem a pelo menos um dos requisitos.

### Loop Over Items — envio dos e-mails de aprovação

Os candidatos aprovados seguem para um nó de Loop Over Items, responsável por percorrer os itens individualmente.

Em seguida, o nó Send a Message do Gmail envia um e-mail personalizado para cada candidato, comunicando sua aprovação para a próxima fase do processo seletivo.

### Aggregate — organização dos candidatos não aprovados

Os candidatos que não atendem aos requisitos seguem para o nó Aggregate.

Esse nó reúne os dados de vários itens em uma estrutura agregada, permitindo organizar os nomes dos candidatos em uma única lista, em vez de trabalhar com cada registro separadamente.

### Gmail — envio da lista ao RH

Após a organização dos nomes, outro nó Send a Message do Gmail envia a lista de candidatos não aprovados para o responsável pelo RH.

Assim, a equipe recebe um resumo dos candidatos que não avançaram para a próxima fase, enquanto os aprovados recebem suas comunicações individualmente.

## 4. Resumo do fluxo

A estrutura geral do workflow é:

1. **Schedule Trigger:** inicia a automação no dia e horário definidos.
2. **Google Sheets — Get Rows:** recupera os dados dos candidatos.
3. **IF:** verifica se os candidatos atendem aos critérios de aprovação.
4. **Loop Over Items + Gmail:** percorre os candidatos aprovados e envia e-mails individuais.
5. **Aggregate + Gmail:** reúne os nomes dos candidatos não aprovados e envia a lista ao RH.


## 5. Registro visual

Abaixo está a imagem final do workflow desenvolvido durante o curso. 

<img width="1368" height="561" alt="image" src="https://github.com/user-attachments/assets/6f742066-2a99-4378-8457-8cfbd7a2bb5f" />


