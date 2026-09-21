# Coleção Engenharia Maker Sem Firula

[![Licença MIT](https://img.shields.io/badge/licença-MIT-blue.svg)](LICENSE)
[![Hardware: ESP32](https://img.shields.io/badge/Hardware-ESP32%20Dual--Core-red.svg)](https://www.espressif.com/)
[![RTOS: FreeRTOS](https://img.shields.io/badge/RTOS-FreeRTOS%20Nativo-green.svg)](https://www.freertos.org/)
[![Home Assistant](https://img.shields.io/badge/Integrado-Home%20Assistant-41BDF5.svg)](https://www.home-assistant.io/)
[![Kindle](https://img.shields.io/badge/Amazon-Tetralogia%20Completa-orange.svg)](https://www.amazon.com.br/)
[![EasyEDA](https://img.shields.io/badge/PCB-EasyEDA%20Gerbers-0099ff.svg)](https://easyeda.com/)

Repositório oficial com códigos-fonte em C++, arquivos YAML do ESPHome, esquemáticos elétricos unificados e pacotes industriais Gerber (PCB) que acompanham os quatro volumes da coleção **Engenharia Maker Sem Firula**.

A premissa desta série editorial é eliminar a cultura do "protótipo frágil de internet" e capacitar o leitor com **engenharia física aplicada**: supressão eletromagnética, contenção de ruído indutivo, contagem em silício por hardware, arquiteturas multitarefa concorrentes no FreeRTOS e controle cinemático determinístico de tempo real.

---

## 📚 A Tetralogia Completa

```text
A JORNADA EVOLUTIVA DA COLEÇÃO:

   [ VOLUME 1: DOMÓTICA RESIDENCIAL ]
   A Fundação de Confiabilidade Local:
   Isolamento óptico, supressão de arcos de 60Hz, presença por radar mmWave e ESPHome local.
                  │
                  ▼
   [ VOLUME 2: ALIMENTAÇÃO E POTÊNCIA ]
   A Infraestrutura Energética do Robô:
   Física de baterias Li-ion 18650, reguladores Buck com filtro LC, drivers MOSFET e Star Ground.
                  │
                  ▼
   [ VOLUME 3: PERCEPÇÃO E SOBREVIVÊNCIA ]
   A Reatividade em Tempo Real:
   Fim do pulseIn(), lasers Time-of-Flight multi-I2C, bumpers com interrupção e Subsumpção de Brooks.
                  │
                  ▼
   [ VOLUME 4: ODOMETRIA E MAPEAMENTO (SLAM) ]
   A Consciência Métrica Espacial:
   Encoders PCNT em silício, malha fechada PID a 100 Hz, fusão com IMU, Log-Odds 2D e WebSockets.
```

---

### [Volume 1: Domótica Sem Nuvem](./Livro-01-Domotica-Sem-Nuvem)
*Automação Residencial Robusta com ESP32, Home Assistant e ESPHome*
* **Dores Resolvidas:** Lâmpadas acendendo sozinhas por indução de 60Hz na tubulação, microcontroladores reiniciando por arco elétrico de relés, falsos positivos de sensores PIR e atrasos de execução por uso de `delay()`.
* **Destaques Técnicos:** Isolamento galvânico real com jumper `JD-VCC`, filtros Snubber RC com varistores MOV, presença humana real por radar mmWave (LD2410 a 24 GHz), debounce elétrico por hardware e PCB dedicada para caixa 4x2 com ranhuras de isolamento de ar (*milling slots*).
* 🔗 [Ver no Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_1)

---

### [Volume 2: Alimentação Sem Reinicializações](./Livro-02-Alimentacao-Sem-Reinicializacoes)
*Baterias, Reguladores Chaveados e Ruído Elétrico em Robôs Móveis*
* **Dores Resolvidas:** *Brownout Reset* no arranque de motores, reguladores lineares que fervem (LM7805/AMS1117), perda de mais de 3V com pontes H bipolares obsoletas (L298N) e instabilidade provocada por servomotores.
* **Destaques Técnicos:** Dimensionamento de Li-ion 18650 com BMS 2S, conversores Step-Down Buck síncronos com filtro LC secundário pós-chaveamento, drivers MOSFET (TB6612FNG), absorção de *Back-EMF* por diodos Schottky SS34, topologia de Ponto Único de Terra (*Star Grounding*) e controlador dedicado PCA9685 via I2C.
* 🔗 [Ver no Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_2)

---

### [Volume 3: Navegação Móvel que Funciona](./Livro-03-Navegacao-Movel-Que-Funciona)
*Sensores e Desvio de Obstáculos em Robôs Móveis*
* **Dores Resolvidas:** Congelamento da CPU por até 30ms com `pulseIn()`, paredes diagonais invisíveis para o ultrassom (reflexão especular), paralisia por árvores confusas de `if/else`, quedas em escadas e travamento da CPU por colisão no barramento I2C.
* **Destaques Técnicos:** Driver de ultrassom orientado a eventos por interrupções externas (`attachInterrupt`), matriz multi-sensor Time-of-Flight a laser (VL53L0X) com chaveamento dinâmico de endereços via pinos `XSHUT`, bumpers de impacto mecânico com corte imediato de tração, sensores de abismo TCRT5000 com histerese analógica, arquitetura de decisão por Subsumpção de Rodney Brooks e autocura de barramento (*I2C Bus Clear*).
* 🔗 [Ver no Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_3)

---

### [Volume 4: Mapeamento e Odometria Sem Deriva](./Livro-04-Mapeamento-Odometria-Sem-Deriva)
*Encoders em Malha Fechada, Controle PID, Fusão com IMU e Mapeamento 2D*
* **Dores Resolvidas:** Robô puxando para o lado em linha reta, perda de passos de encoder em alta velocidade, saturação integral (*Integrator Windup*), acúmulo de erro de posição em curvas, deriva térmica do giroscópio e dependência de computadores de bordo caros com Linux/ROS para visualizar mapas.
* **Destaques Técnicos:** Decodificação de quadratura 4X em silício dedicado via periférico **PCNT** (zero carga de CPU), malhas fechadas de velocidade com **PID a 100 Hz** com *Anti-Windup Clamping*, cinemática diferencial com **Integração pelo Ponto Médio (Runge-Kutta 2ª Ordem)**, calibração experimental de erros de diâmetro e bitola pelo **Protocolo UMBmark de Borenstein**, fusão inercial com giroscópio **MPU-6050** via Filtro Complementar, grade de ocupação 2D em **Log-Odds** quantizada em `int8_t` (economia de 85% de RAM), raycasting ultrarrápido com o algoritmo de **Bresenham**, servidor embarcado assíncrono via **WebSockets e Canvas HTML5**, e arquitetura **Dual-Core no FreeRTOS** com sincronização via *Mutex*.
* 🔗 [Ver no Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_4)

---

## ⚡ Matriz Mestre de Pinagem Unificada do Robô (ESP32)

Esta distribuição de pinos foi projetada para que os circuitos dos **Volumes 2, 3 e 4 coexistam simultaneamente no mesmo chassi sem conflitos de barramento ou problemas com os *strapping pins* de boot**:

| Periférico | Função no Chassi | Pino ESP32 | Tipo / Modo | Volumes |
| :--- | :--- | :---: | :---: | :---: |
| **Barramento I2C** | Linha de Dados (`SDA`) | `GPIO 21` | Dreno Aberto (Pull-up 2.2k) | V2, V3, V4 |
| **Barramento I2C** | Linha de Clock (`SCL`) | `GPIO 22` | Dreno Aberto (Pull-up 2.2k) | V2, V3, V4 |
| **Driver Motores** | PWM Esquerdo (`PWMA`) | `GPIO 19` | Saída LEDC a 20 kHz | V2, V3, V4 |
| **Driver Motores** | Sentido Motor Esq (`AIN1`) | `GPIO 18` | Saída Digital Lógica | V2, V3, V4 |
| **Driver Motores** | Sentido Motor Esq (`AIN2`) | `GPIO 5`  | Saída Digital Lógica | V2, V3, V4 |
| **Driver Motores** | PWM Direito (`PWMB`) | `GPIO 16` | Saída LEDC a 20 kHz | V2, V3, V4 |
| **Driver Motores** | Sentido Motor Dir (`BIN1`) | `GPIO 4`  | Saída Digital Lógica | V2, V3, V4 |
| **Driver Motores** | Sentido Motor Dir (`BIN2`) | `GPIO 27` | Saída Digital Lógica | V2, V3, V4 |
| **Driver Motores** | Standby / Corte Rápido (`STBY`)| `GPIO 23` | Saída Digital (*Active HIGH*) | V2, V3, V4 |
| **Ultrassom HC-SR04**| Disparo de Gatilho (`TRIG`)| `GPIO 13` | Saída Digital (Pulso 10µs) | V3, V4 |
| **Ultrassom HC-SR04**| Captura do Eco (`ECHO`)| `GPIO 14` | **Interrupção Externa (ISR)** | V3, V4 |
| **Laser ToF Esq** | Shutdown (`XSHUT_1`) | `GPIO 25` | Saída Digital (Boot -> 0x30) | V3, V4 |
| **Laser ToF Dir** | Shutdown (`XSHUT_2`) | `GPIO 26` | Saída Digital (Boot -> 0x31) | V3, V4 |
| **Bumper Mecânico** | Chave Esquerda | `GPIO 32` | **Interrupção Externa (ISR)** | V3, V4 |
| **Bumper Mecânico** | Chave Direita | `GPIO 33` | **Interrupção Externa (ISR)** | V3, V4 |
| **Telemetria Bateria**| Divisor Resistivo Pack Li-ion | `GPIO 35` | Entrada ADC1 (*Input-Only*) | V2, V3, V4 |
| **Sensor de Abismo**| TCRT5000 Esquerdo | `GPIO 34` | Entrada ADC1 (*Input-Only*) | V3, V4 |
| **Sensor de Abismo**| TCRT5000 Direito | `GPIO 39` | Entrada ADC1 (Sensor VN) | V3, V4 |
| **Encoder Quadratura**| Motor Esq - Canal A | `GPIO 15` | Entrada PCNT (Unidade 0) | V4 |
| **Encoder Quadratura**| Motor Esq - Canal B | `GPIO 2`  | Entrada PCNT (Unidade 0) | V4 |
| **Encoder Quadratura**| Motor Dir - Canal A | `GPIO 36` | Entrada PCNT (Unidade 1 - VP) | V4 |
| **Encoder Quadratura**| Motor Dir - Canal B | `GPIO 17` | Entrada PCNT (Unidade 1) | V4 |

*(Nota: O Volume 1 é um nó residencial independente instalado em caixas 4x2 de parede. Ele utiliza relé em GPIO 23, tecla com debounce em GPIO 18 e o radar mmWave na UART2 nos GPIOs 16/17).*

---

## 📁 Estrutura Completa de Pastas do Repositório

```text
engenharia-maker-livros/
├── .gitignore
├── LICENSE
├── README.md
│
├── Livro-01-Domotica-Sem-Nuvem/
│   ├── README.md
│   ├── firmware/
│   │   ├── 01_teste_rele_seguro/
│   │   │   └── 01_teste_rele_seguro.ino
│   │   ├── 02_no_iluminacao_resiliente/
│   │   │   └── 02_no_iluminacao_resiliente.ino
│   │   ├── 03_no_multisensor_mmwave/
│   │   │   └── 03_no_multisensor_mmwave.ino
│   │   └── 04_esphome/
│   │       └── modulo_quarto.yaml
│   └── hardware/
│       ├── esquematicos/
│       │   └── esquematico_caixa_4x2.pdf
│       └── gerber_pcb/
│           ├── Gerber_Modulo_Domotica_4x2.zip
│           └── README_fabricacao.md
│
├── Livro-02-Alimentacao-Sem-Reinicializacoes/
│   ├── README.md
│   ├── firmware/
│   │   ├── 01_monitor_bateria_basico/
│   │   │   └── 01_monitor_bateria_basico.ino
│   │   ├── 02_driver_motor_tb6612/
│   │   │   └── 02_driver_motor_tb6612.ino
│   │   ├── 03_failsafe_energia_ema/
│   │   │   └── 03_failsafe_energia_ema.ino
│   │   ├── 04_controlador_servos_pca9685/
│   │   │   └── 04_controlador_servos_pca9685.ino
│   │   └── 05_diagnostico_boot_reason/
│   │       └── 05_diagnostico_boot_reason.ino
│   └── hardware/
│       ├── esquematicos/
│       │   └── esquematico_pdb_blindada.pdf
│       └── gerber_pcb/
│           ├── Gerber_PDB_Robo_50x50.zip
│           └── README_fabricacao.md
│
├── Livro-03-Navegacao-Movel-Que-Funciona/
│   ├── README.md
│   ├── firmware/
│   │   ├── 01_ultrassom_assincrono/
│   │   │   └── 01_ultrassom_assincrono.ino
│   │   ├── 02_laser_multitof_xshut/
│   │   │   └── 02_laser_multitof_xshut.ino
│   │   ├── 03_subsumption_core/
│   │   │   └── 03_subsumption_core.ino
│   │   ├── 04_i2c_bus_recovery/
│   │   │   └── 04_i2c_bus_recovery.ino
│   │   └── 05_master_navigation_core/
│   │       └── 05_master_navigation_core.ino
│   └── hardware/
│       ├── esquematicos/
│       │   └── esquematico_shield_frontal.pdf
│       └── gerber_pcb/
│           ├── Gerber_Shield_Frontal_Navegacao.zip
│           └── README_fabricacao.md
│
└── Livro-04-Mapeamento-Odometria-Sem-Deriva/
    ├── README.md
    ├── firmware/
    │   ├── 01_closed_loop_motor_pid/
    │   │   └── 01_closed_loop_motor_pid.ino
    │   ├── 02_differential_odometry/
    │   │   ├── differential_odometry.h
    │   │   └── differential_odometry.ino
    │   ├── 03_umbmark_calibration/
    │   │   └── 03_umbmark_calibration.ino
    │   ├── 04_imu_complementary_filter/
    │   │   └── 04_imu_complementary_filter.ino
    │   ├── 05_async_mapper_server/
    │   │   ├── occupancy_grid_2d.h
    │   │   └── async_mapper_server.ino
    │   └── 06_master_slam_firmware/
    │       └── 06_master_slam_firmware.ino
    └── hardware/
        ├── esquematicos/
        │   └── esquematico_conexao_encoders_imu.pdf
        └── web_interface/
            └── index.html
```

---

## 🛠️ Requisitos de Software e Bibliotecas

1. **Ambiente de Desenvolvimento:** Arduino IDE 2.3+ ou PlatformIO sobre VS Code.
2. **Pacote de Placas:** Espressif ESP32 Core versão `2.0.14` ou superior.
3. **Bibliotecas Oficiais (Instalar via Library Manager):**
   * `PubSubClient` (por Nick O'Leary)
   * `Adafruit AHTX0` e `Adafruit BusIO`
   * `Adafruit PWM Servo Driver Library`
   * `Adafruit_VL53L0X`
   * `ESPAsyncWebServer` e `AsyncTCP` (por me-no-dev / mathieucarbou)

---

## 📦 Manufatura das Placas de Circuito Impresso (PCB)

Cada projeto acompanha seus arquivos industriais de produção na pasta `hardware/gerber_pcb/`:
* **Livro 1:** Módulo de Relé com Isolamento Óptico para Caixa 4x2 Residencial.
* **Livro 2:** Power Distribution Board (PDB) de 50x50 mm para até 10A com Star Grounding.
* **Livro 3:** Shield Frontal de Navegação em semi-arco com suporte angulado a $\pm 30^\circ$.

Envie os arquivos `.zip` diretamente para fabricantes de PCB (como JLCPCB ou PCBWay).  
*Parâmetros recomendados:* 2 camadas (*2-Layer*), espessura de 1.6 mm, acabamento HASL Lead-Free, espessura de cobre de 1 oz (ou 2 oz para a PDB do Livro 2).

---

## 📄 Licença

Todo o código-fonte, esquemáticos e arquivos de layout de placas são distribuídos sob a **Licença MIT** (livres para fins educacionais, pessoais e comerciais). Consulte o arquivo [LICENSE](LICENSE) para detalhes completos.
