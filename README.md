# 🩺 Sprint 2 CarePlus Edge Computing e Computer Systems
Este projeto apresenta uma arquitetura completa de um sistema de monitoramento de sinais vitais baseado em Internet das Coisas (IoT). O sistema coleta dados fisiológicos em tempo real (BPM e Temperatura), processa-os na borda (Edge), envia de forma segura para a nuvem e os disponibiliza em um dashboard para profissionais de saúde.

👨‍💻 Autor
Desenvolvido por:

RM567113 - Helton Pacheco dos Santos 
RM567754 - Geovanna Caroline Lima Santos
RM566903 - Gustavo Firmino Barbosa

🏗️ Arquitetura do Sistema
O sistema é dividido em quatro camadas principais:

1. Camada Edge (Dispositivo IoT)
Hardware: Microcontrolador ESP32.

Sensores: Captura de BPM (Batimentos por Minuto) e Temperatura.

Display: SSD1306 (OLED) via I2C para visualização local imediata.

Lógica: Firmware desenvolvido em C/C++.

2. Comunicação e Broker MQTT
Protocolo: MQTT com criptografia TLS (Porta 8883) para garantir a privacidade dos dados médicos.

Broker: HiveMQ Cloud (Gerenciamento em nuvem com autenticação segura).

Payload: Formato JSON.

Tópicos: careplus/bpm e careplus/temp.

3. Camada Back-end (Processamento e Persistência)
Integração: Node-RED para orquestração do fluxo de dados.

Contexto: FIWARE Orion Context Broker para gestão de dados em tempo real.

Banco de Dados: MongoDB (NoSQL) para persistência e histórico dos sinais vitais.

Regras de Negócio: Lógica para detecção de anomalias e alertas.

4. Camada Application
Interface: Dashboard interativo para acompanhamento em tempo real.

Protocolos de Entrega: REST e WebSockets para baixa latência.

📊 Fluxograma de Funcionamento
Snippet de código
graph TD
    A[Sensores] --> B[ESP32]
    B --> C[Visualização Local]
    B -- MQTT/TLS --> D[HiveMQ Cloud]
    D -- Subscribe --> E[Back-end]
    E --> F[Node-RED/FIWARE]
    F --> G[MongoDB]
    G --> H[Dashboard Médico]
🛠️ Tecnologias Utilizadas
Linguagens: C++, JavaScript.

IoT: ESP32, Protocolo MQTT, Sensores de Sinais Vitais.

Infraestrutura: HiveMQ, Node-RED, FIWARE.

Banco de Dados: MongoDB.

Segurança: TLS/SSL, Autenticação via Usuário/Senha.

🚀 Como Executar o Projeto
Configuração do Hardware:

Conecte os sensores ao ESP32 conforme o esquema [link para esquema].

Suba o código disponível na pasta /firmware configurando suas credenciais Wi-Fi e HiveMQ.

Configuração do Back-end:

Importe o fluxo do Node-RED disponível em /backend/flows.json.

Certifique-se de que a instância do MongoDB e FIWARE estão rodando.

Visualização:

Acesse o dashboard em localhost:porta para ver os dados em tempo real.

📄 Licença
Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.


