# Simulação de Sensor de Gás com ESP32 (Challenge Hermes Reply - Sprint 2)

Projeto desenvolvido como parte do desafio Hermes Reply (Fase 4), com foco em simular um sistema embarcado de coleta de dados utilizando o ESP32 e sensor de gás MQ2, em ambiente virtual (Wokwi), com análise dos dados em Python (Google Colab).

---

## 🎯 Objetivo

Simular a leitura de dados de um sensor de gás em ambiente industrial, utilizando o ESP32 e um sensor de gás virtual (MQ2, equivalente ao MQ135), com posterior visualização dos dados e análise gráfica.

---

## 🧪 Lista de Sensores Virtuais Utilizados e Justificativa

### • Sensor MQ2 (simulando o MQ135)

O sensor MQ2 foi utilizado no Wokwi como alternativa ao MQ135, pois ambos têm funcionalidades semelhantes na detecção de gases em ambientes industriais.

> “Escolhemos o sensor DHT22 por ser amplamente utilizado em ambientes industriais para monitorar temperatura e umidade, fatores críticos no controle ambiental de equipamentos.”

> Para a simulação do ambiente industrial, optamos por utilizar o sensor virtual **MQ135**, que é amplamente empregado em sistemas de monitoramento da qualidade do ar. Esse sensor é capaz de detectar uma variedade de gases tóxicos e inflamáveis, como **amônia (NH₃), dióxido de carbono (CO₂), benzeno, fumaça e vapores industriais**.

Em fábricas e ambientes industriais fechados — como **linhas de pintura, áreas de soldagem, setores de estocagem de produtos químicos ou salas com pouca ventilação** — o controle da qualidade do ar é essencial para garantir **segurança operacional e saúde dos trabalhadores**.

A escolha do MQ135 (simulado aqui com MQ2) permite representar esse cenário da **Indústria 4.0**, onde sensores embarcados conectados ao ESP32 monitoram em tempo real a presença de gases e a pureza do ar, possibilitando **ações automatizadas e alertas preventivos**.

---

## 🔌 Esquema Básico do Circuito Elétrico

O sensor MQ2 foi conectado à placa ESP32 da seguinte forma:

| Pino do Sensor MQ2 | Pino do ESP32 |
|--------------------|---------------|
| VCC                | 3.3V          |
| GND                | GND           |
| AOUT               | GPIO34        |

📷 **Imagem do circuito:**  
/imagens/circuito.png

---

## 💻 Código-Fonte Representativo

A leitura foi feita por meio do pino analógico AOUT do sensor MQ2, conectado ao GPIO34 do ESP32. Os dados foram exibidos via Monitor Serial.

```cpp
#define MQ2_PIN 34

void setup() {
  Serial.begin(115200);
}

void loop() {
  int leitura = analogRead(MQ2_PIN);
  float tensao = (leitura / 4095.0) * 3.3;

  Serial.print("Leitura MQ2: ");
  Serial.print(leitura);
  Serial.print(" | Tensão: ");
  Serial.print(tensao, 2);
  Serial.println(" V");

  delay(1000);
}
```

---

## 🔍 Leitura dos Dados na Simulação

A leitura é feita com `analogRead()`, convertendo a leitura analógica (0 a 4095) em tensão (0 a 3.3V).  
A concentração de gás é ajustável manualmente pelo controle deslizante (slider) do sensor no Wokwi, simulando diferentes cenários industriais.

📷 **Print do Serial Monitor:**  
/imagens/serial_monitor.png

---

## 📊 Análise Gráfica

Os dados foram copiados do Serial Monitor, tratados em Python com `pandas` e visualizados com `matplotlib`.

📈 **Gráfico gerado:**  
/analise/grafico_sensor_gas.png

---

## 🔗 Links do Projeto

- **Notebook Colab:**  
  https://colab.research.google.com/drive/1BJvYSt8V64tG8Hnme5tiAllYLUWOoj9b?usp=sharing

- **Simulação no Wokwi:**  
  https://wokwi.com/projects/433486118346911745

---

## ✅ Conclusão

O projeto demonstrou com sucesso a simulação de um sistema de monitoramento da qualidade do ar em um ambiente industrial utilizando o ESP32. A simulação permitiu entender o fluxo de leitura analógica de sensores, a simulação de dados e a análise gráfica com Python, cumprindo os requisitos do desafio proposto pela Hermes Reply na Fase 4.

---

## 👨‍💻 Integrantes

- **Flavia Nunes Bocchino** – RM564213  
- **Pedro Henrique Zani** – RM564956  
- **Felipe Menezes** – RM557891

---

## 🎓 Curso

**FIAP | Enterprise Challenge 2025.1**  
Fase 4 – Simulação e coleta de dados com ESP32  
Projeto acadêmico em parceria com a Hermes Reply
