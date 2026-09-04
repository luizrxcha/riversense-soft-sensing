\# Sensoriamento Virtual de Poluentes Hídricos: Predição via Machine Learning com Sensores de Baixo Custo em Rios Brasileiros 🌊💻



Este repositório contém os códigos, firmwares e conjuntos de dados do projeto de Iniciação Científica desenvolvido no \*\*Instituto Federal de Educação, Ciência e Tecnologia de São Paulo (IFSP) - Campus Bragança Paulista\*\*, sob fomento do \*\*Conselho Nacional de Desenvolvimento Científico e Tecnológico (CNPq)\*\* \[1].



O projeto está alinhado diretamente à \*\*Meta 6.3 da Agenda 2030 da Organização das Nações Unidas (ONU)\*\*, visando apoiar o avanço do \*\*Indicador 6.3.2\*\* (proporção de corpos hídricos com boa qualidade ambiental) através do monitoramento em tempo real e de baixo custo \[2, 3].



\---



\## 📋 Sobre o Projeto



O monitoramento contínuo de nutrientes críticos (como Nitrogênio e Fósforo) e contaminação microbiológica (\*E. coli\*) em rios brasileiros esbarra em barreiras técnico-financeiras extremas, devido ao custo proibitivo de estações automatizadas comerciais \[2, 4].



Este projeto utiliza a metodologia de \*\*Sensoriamento Virtual (Soft-Sensing)\*\* \[2, 5]:

1\. \*\*Aquisição Econômica:\*\* Sensores físicos básicos de Nível 1 (pH, temperatura, turbidez e condutividade elétrica/TDS) capturam as variáveis de fácil medição \[2, 6].

2\. \*\*Inteligência Artificial:\*\* Um modelo supervisionado \*\*Random Forest\*\* mapeia as interações matemáticas não-lineares dessas variáveis básicas para prever indiretamente a presença de poluentes complexos \[2, 7].

3\. \*\*Edge AI / Computação na Borda:\*\* O modelo matemático é portado de Python para C/C++ e embarcado no microcontrolador local \*\*ESP32\*\*, garantindo inferências locais instantâneas e autonomia energética \[8, 9].

4\. \*\*Protótipo Mecânico:\*\* A eletrônica é encapsulada em uma boia estanque baseada na arquitetura \*\*AquaNode\*\*, alimentada por um sistema solar fotovoltaico com rotinas de baixo consumo (\*deep sleep\*) \[9, 10].



\---



\## 📂 Estrutura de Pastas



```text

riversense-soft-sensing/

├── firmware/                 # Firmwares do microcontrolador local

│   ├── src/                  # Código-fonte principal (.ino ou .cpp) do ESP32

│   └── libraries/            # Bibliotecas de calibração e comunicação

├── notebooks/                # Jupyter Notebooks em Python para ciência de dados

│   ├── 01\_analise\_exploratoria.ipynb  # Tratamento e plotagem dos sinais brutos

│   └── 02\_treino\_random\_forest.ipynb  # Treinamento e exportação do modelo

├── data/                     # Dados coletados nas simulações experimentais

│   ├── raw/                  # Dataset bruto gerado na bancada de ensaios

│   └── processed/            # Dados normalizados e rotulados

├── models/                   # Modelos preditivos gerados

│   ├── random\_forest.pkl     # Modelo salvo em formato binário Python

│   └── model\_embedded.h      # Matriz estática de decisão C/C++ para o ESP32

├── docs/                     # Documentações do projeto

│   ├── esquematicos/         # Esquemas elétricos e pinagem do hardware

│   └── artigos/              # PDF do projeto de IC e referências acadêmicas

├── .gitignore                # Arquivos ignorados pelo controle de versão do Git

└── README.md                 # Apresentação do repositório (esta vitrine)

🧪 Metodologia e Coleta de Dados (Bancada)

Para treinar a Inteligência Artificial, o projeto prevê três ensaios práticos controlados em laboratório para simulação de cenários de poluição

:

Picos de Salinidade: Adição gradual de cloreto de sódio para alterar a condutividade elétrica e o TDS

.

Assoreamento e Erosão: Introdução controlada de lama/solo para forçar a variação de turbidez

.

Carga Orgânica: Adição de água de aquário rica em dejetos para monitorar alterações acopladas no pH e na condutividade causadas por compostos nitrogenados

.

Os dados lidos no ESP32 são limpos por filtros digitais de média móvel, rotulados e exportados para o computador para estruturar o dataset de treinamento

.

🛠️ Conexões Elétricas Recomendadas

A pinagem recomendada para montagem e aquisição de dados via ADC1 no ESP32

&#x20;para evitar conflitos com o hardware de comunicação sem fio:

Sensor / Componente

Tipo de Sinal

Pino Recomendado

Alimentação

Observação Física

TDS / Condutividade

Analógico

GPIO 34

3.3V (ou 5V)

Leitura direta de sinal analógico.

pH (Módulo 4502c)

Analógico

GPIO 35

5V

Leitura do pino Po de saída analógica.

Turbidez (Óptico)

Analógico

GPIO 32

5V

Requer divisor de tensão (3.3V) ou conversor lógico.

DS18B20 (Temperatura)

Digital (1-Wire)

GPIO 4

3.3V (ou 5V)

Exige resistor de pull-up de 4.7kΩ entre Dados e VCC.

⚖️ Aviso de Transparência (Portaria CNPq nº 2664/2026)

Ferramentas de Inteligência Artificial Generativa foram utilizadas estritamente para auxílio na estruturação de tópicos e revisão gramatical da escrita deste projeto, sendo o autor integralmente responsável pelo conteúdo técnico, código final e integridade da pesquisa científica aqui apresentada

.

🧑‍🔬 Equipe e Contatos

Orientando/Pesquisador: \[Seu Nome] - \[Seu E-mail]

Orientador: Prof. Dr. Alexandre Tomazati Oliveira

&#x20;- tomazati@ifsp.edu.br

Instituição: Instituto Federal de São Paulo (IFSP) - Campus Bragança Paulista



\---



\### Como aplicar esse arquivo ao seu projeto?

1\. Abra a pasta `riversense-soft-sensing` no seu computador utilizando o seu editor de códigos (como o \*\*VS Code\*\*).

2\. Crie um arquivo com o nome exato \*\*`README.md`\*\* na raiz da pasta.

3\. Copie o bloco de código acima e cole dentro dele.

4\. Lembre-se de substituir `\[Seu Nome]` e `\[Seu E-mail]` na seção final de \*\*Equipe e Contatos\*\*.

5\. Salve o arquivo e faça o envio para o seu GitHub pelo terminal com os comandos:

&#x20;  ```bash

&#x20;  git add README.md

&#x20;  git commit -m "docs: adiciona o README com a fundamentacao do projeto"

&#x20;  git push origin main

