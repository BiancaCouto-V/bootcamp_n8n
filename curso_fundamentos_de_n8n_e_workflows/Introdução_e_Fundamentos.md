# Introdução ao n8n e Workflows

Neste módulo, foram apresentados os conceitos básicos do n8n, as formas de instalação da plataforma e como criar e organizar workflows simples.

## 1. Primeiros passos com n8n

O n8n é uma plataforma de automação de workflows (fluxos de trabalho) que permite conectar diferentes aplicações e automatizar tarefas. Também é possível adicionar recursos de inteligência artificial aos fluxos.

A construção dos workflows acontece por meio de nós (*nodes*) que são conectados para definir as etapas que o programa deve executar. O n8n é uma ferramenta low-code, ou seja, permite criar automações visualmente, sem precisar escrever código para todas as etapas.

### Formas de instalar o n8n

Existem três maneiras principais de utilizar o n8n:

- **Local setup:** instalação na própria máquina. Não exige contratar um servidor de nuvem, mas a execução dos workflows depende de o computador estar ligado. Existem opções como a versão desktop, instalação via Node.js e Docker.
- **n8n Cloud:** versão hospedada pelo próprio n8n. É mais simples de configurar, pois não exige que o usuário cuide da infraestrutura. A utilização depende de um plano contratado, com cobrança baseada nas execuções, conforme as condições do plano.
- **Self-hosting:** instalação em um servidor próprio ou contratado. Nesse caso, os workflows podem continuar executando mesmo quando o computador pessoal está desligado. Em contrapartida, é necessário cuidar da configuração e da manutenção da infraestrutura, e os custos dependem do servidor escolhido.

A instalação via Docker é uma alternativa interessante porque utiliza contêineres e pode facilitar a migração do ambiente local para um servidor.

Também foi comentado que o n8n utiliza um banco de dados para armazenar informações internas e que as *migrations* são utilizadas para gerenciar alterações na estrutura desse banco.

## 2. Criação de workflows simples

Todo workflow precisa de algum tipo de gatilho (*trigger*) para iniciar sua execução, seja um evento, um agendamento ou outra condição configurada.

Os nós são conectados para que os dados de um passo sejam utilizados pelo próximo. De maneira geral, cada nó possui três partes principais:

- **Input:** os dados recebidos pelo nó, que podem incluir parâmetros de entrada.
- **Process:** o processamento realizado pelo nó, de acordo com sua função e configuração.
- **Output:** os dados produzidos após o processamento, que podem ser encaminhados para o próximo nó.

Os parâmetros configurados em cada nó influenciam seu funcionamento. Alguns são utilizados para definir os dados de entrada, enquanto outros controlam o processamento.

### JSON e transferência de dados

Os dados passam de um nó para outro em uma estrutura que utiliza JSON (*JavaScript Object Notation*), um formato bastante utilizado para trocar informações entre sistemas.

Um objeto JSON é formado por pares de chave e valor e utiliza chaves `{}` para delimitar sua estrutura.

Além de ser importante para a transferência de dados entre etapas, o JSON também aparece nos arquivos de exportação dos workflows do n8n.

## 3. Boas práticas de organização

Durante a criação dos workflows, foram apresentadas algumas práticas que ajudam a entender melhor o fluxo e facilitam sua manutenção:

- **Nomear os nós:** utilizar nomes que indiquem claramente a ação realizada em cada etapa.
- **Organizar os nós visualmente:** usar a opção *Tidy Up* para alinhar e organizar a estrutura do workflow.
- **Adicionar notas e stickers:** registrar explicações, observações e tarefas pendentes.
- **Separar as etapas por regiões:** agrupar visualmente os nós que fazem parte de uma mesma fase do processo.

Essas práticas ajudam principalmente na hora de revisar uma automação, entender o que cada etapa faz e encontrar possíveis erros durante a depuração (*debugging*).

### Exportação e importação de workflows

O n8n permite exportar workflows em arquivos JSON. Esses arquivos podem ser abertos em outros editores, utilizados como backup ou importados novamente em outro ambiente do n8n.

Isso também facilita a migração de automações entre ambientes.

## 4. Workflow desenvolvido

Abaixo está a imagem do workflow construído durante as atividades práticas do módulo.

<img width="902" height="518" alt="image" src="https://github.com/user-attachments/assets/b15a65bf-9d0c-4588-83f3-e3cf9dab4e39" />


## Resumo do módulo

Neste primeiro módulo, foram apresentados os conceitos iniciais do n8n, suas opções de instalação, a estrutura dos workflows, o funcionamento dos nós e o uso do JSON para transferir dados e exportar automações. Também foram abordadas boas práticas para organizar, documentar e manter os fluxos criados.
