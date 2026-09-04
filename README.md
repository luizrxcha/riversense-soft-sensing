# Sensoriamento Virtual de Poluentes Hídricos: Predição via Machine Learning com Sensores de Baixo Custo em Rios Brasileiros 🌊

Este repositório contém os códigos, firmwares e conjuntos de dados do projeto de Iniciação Científica desenvolvido no **Instituto Federal de Educação, Ciência e Tecnologia de São Paulo (IFSP) - Campus Bragança Paulista**, sob fomento do **Conselho Nacional de Desenvolvimento Científico e Tecnológico (CNPq)**.

O projeto está alinhado diretamente à **Meta 6.3 da Agenda 2030 da Organização das Nações Unidas (ONU)**, visando apoiar o avanço do **Indicador 6.3.2** (proporção de corpos hídricos com boa qualidade ambiental) através do monitoramento em tempo real e de baixo custo.

---

## 📋 Sobre o Projeto

O monitoramento contínuo de nutrientes críticos (como Nitrogênio e Fósforo) e contaminação microbiológica (*E. coli*) em rios brasileiros esbarra em barreiras técnico-financeiras extremas, devido ao custo proibitivo de estações automatizadas comerciais.

Este projeto utiliza a metodologia de **Sensoriamento Virtual (Soft-Sensing)**:

1. **Aquisição Econômica:** Sensores físicos básicos de Nível 1 (pH, temperatura, turbidez e condutividade elétrica/TDS) capturam as variáveis de fácil medição.
2. **Inteligência Artificial:** Um modelo supervisionado **Random Forest** mapeia as interações matemáticas não-lineares dessas variáveis básicas para prever indiretamente a presença de poluentes complexos.
3. **Edge AI / Computação na Borda:** O modelo matemático é portado de Python para C/C++ e embarcado no microcontrolador local **ESP32**, garantindo inferências locais instantâneas e autonomia energética.
4. **Protótipo Mecânico:** A eletrônica é encapsulada em uma boia estanque baseada na arquitetura **AquaNode**, alimentada por um sistema solar fotovoltaico com rotinas de baixo consumo (*deep sleep*).

---

## 📂 Estrutura de Pastas

```text
riversense-soft-sensing/
├── firmware/                 # Firmwares do microcontrolador local
│   ├── src/                  # Código-fonte principal (.ino ou .cpp) do ESP32
│   └── libraries/            # Bibliotecas de calibração e comunicação
├── notebooks/                # Jupyter Notebooks em Python para ciência de dados
│   ├── 01_analise_exploratoria.ipynb  # Tratamento e plotagem dos sinais brutos
│   └── 02_treino_random_forest.ipynb  # Treinamento e exportação do modelo
├── data/                     # Dados coletados nas simulações experimentais
│   ├── raw/                  # Dataset bruto gerado na bancada de ensaios
│   └── processed/            # Dados normalizados e rotulados
├── models/                   # Modelos preditivos gerados
│   ├── random_forest.pkl     # Modelo salvo em formato binário Python
│   └── model_embedded.h      # Matriz estática de decisão C/C++ para o ESP32
├── docs/                     # Documentações do projeto
│   ├── esquematicos/         # Esquemas elétricos e pinagem do hardware
│   └── artigos/              # PDF do projeto de IC e referências acadêmicas
├── .gitignore                # Arquivos ignorados pelo controle de versão do Git
└── README.md                 # Apresentação do repositório (esta vitrine)
```
🧪 Metodologia e Coleta de Dados (Bancada)
Para treinar a Inteligência Artificial, o projeto prevê três ensaios práticos controlados em laboratório para simulação de cenários de poluição:
Picos de Salinidade: Adição gradual de cloreto de sódio para alterar a condutividade elétrica e o TDS.
Assoreamento e Erosão: Introdução controlada de lama/solo para variar a turbidez óptica.
Carga Orgânica: Adição de água de aquário rica em dejetos para monitorar alterações acopladas no pH e na condutividade causadas por compostos nitrogenados.
Os dados lidos no ESP32 são limpos por filtros digitais de média móvel, rotulados e exportados para o computador para estruturar o dataset de treinamento.
🛠️ Conexões Elétricas Recomendadas
A pinagem recomendada para montagem e aquisição de dados via ADC1 no ESP32 para evitar conflitos com o hardware de comunicação sem fio:
Sensor / Componente
Tipo de Sinal
Pino Recomendado
Alimentação
Observação Física
TDS (Condutividade)
Analógico
GPIO 34
3.3V (ou 5V)
Ligar o pino de sinal (Ao) diretamente na porta 34.
pH (Módulo 4502c)
Analógico
GPIO 35
5V
Ligar o pino Po diretamente na porta 35.
Turbidez (Óptico)
Analógico
GPIO 32
5V
Requer atenção: O sinal de saída precisa passar por um divisor de tensão (resistores) ou conversor lógico antes de entrar na porta 32.
DS18B20 (Temperatura)
Digital (1-Wire)
GPIO 4
3.3V (ou 5V)
Ligar o pino de dados na porta 4. Exige um resistor de 4.7kΩ fazendo uma ponte entre a linha de dados e a linha de VCC.
Nota de Aterramento: Lembre-se de que todos os pinos GND dos sensores e do circuito devem obrigatoriamente estar conectados à mesma trilha azul (terra) da protoboard, que por sua vez deve estar ligada ao GND do ESP32.
⚖️ Aviso de Transparência (Portaria CNPq nº 2664/2026)
Ferramentas de Inteligência Artificial Generativa foram utilizadas estritamente para auxílio na estruturação de tópicos e revisão gramatical da escrita deste projeto, sendo o autor integralmente responsável pelo conteúdo técnico, código final e integridade da pesquisa científica aqui apresentada.
🧑‍🔬 Equipe e Contatos
Orientando/Pesquisador: [Seu Nome] - [Seu E-mail]
Orientador: Prof. Dr. Alexandre Tomazati Oliveira - tomazati@ifsp.edu.br
Instituição: Instituto Federal de São Paulo (IFSP) - Campus Bragança Paulista

4. **Salve o arquivo** (`Ctrl + S`).
5. No seu **Git Bash**, envie a correção digitando os comandos abaixo um por um:

```bash
# 1. Adiciona a correção do README.md
git add README.md

# 2. Registra o commit da correção
git commit -m "docs: corrige formatacao e espacamento do readme"

# 3. Envia para o GitHub
git push origin main
