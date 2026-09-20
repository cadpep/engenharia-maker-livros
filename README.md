# Coleção Engenharia Maker Sem Firula

[![Licença MIT](https://img.shields.io/badge/licença-MIT-blue.svg)](LICENSE)
[![Hardware: ESP32](https://img.shields.io/badge/Hardware-ESP32-red.svg)](https://www.espressif.com/)
[![Home Assistant](https://img.shields.io/badge/Integrado-Home%20Assistant-41BDF5.svg)](https://www.home-assistant.io/)
[![Livros na Amazon](https://img.shields.io/badge/Kindle-Disponível%20no%20KDP-orange.svg)](https://www.amazon.com.br/)

Repositório oficial com os códigos-fonte em C++, arquivos de configuração do ESPHome, esquemáticos e pacotes de manufatura Gerber (PCB) que acompanham os volumes da coleção **Engenharia Maker Sem Firula**.

Esta série de livros foi desenvolvida com foco estrito em **dores reais de engenharia**: sem projetos com leds piscando ou semáforos didáticos, priorizando soluções com proteção contra ruído, arquitetura assíncrona e hardware imune a falhas físicas.

---

## 📚 Livros da Coleção

### [Volume 1: Domótica Sem Nuvem](./Livro-01-Domotica-Sem-Nuvem)
*Foco: Automação Residencial Segura com ESP32 e Home Assistant*
* **Problemas resolvidos:** Reinicializações por ruído de bobina de relé, lâmpadas que acendem sozinhas por indução de 60Hz nos conduítes, atrasos bloqueantes por uso de `delay()` e sensores PIR obsoletos que apagam a luz com ocupantes imóveis.
* **Componentes principais:** ESP32, Módulo Relé optoacoplado com jumper JD-VCC, Snubber RC, Varistor MOV, Radar mmWave LD2410 (24GHz) e sensor I2C AHT20.
* 🔗 [Obtenha o livro digital na Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_1)

### [Volume 2: Alimentação Sem Reinicializações](./Livro-02-Alimentacao-Sem-Reinicializacoes)
*Foco: Baterias, Reguladores Chaveados e Ruído Elétrico em Robôs Móveis*
* **Problemas resolvidos:** *Brownout Reset* no arranque de motores, aquecimento crítico de reguladores lineares (LM7805/AMS1117), perda de tensão pelo driver L298N, ruído indutivo de *Back-EMF* e trepidação (*jitter*) em servomotores.
* **Componentes principais:** Células Li-ion 18650 em pack 2S, BMS 2S 10A, Conversores Step-Down Buck (MP1584EN), Ponte H a MOSFET TB6612FNG, Diodos Schottky SS34 e Controlador I2C PCA9685.
* 🔗 [Obtenha o livro digital na Amazon Kindle](https://www.amazon.com.br/dp/SEU_ASIN_LIVRO_2)

---

## 🛠️ Requisitos de Software

Para compilar e enviar os códigos deste repositório, você precisará de:

1. **Arduino IDE 2.x** (ou extensão do PlatformIO no VS Code):
   * Placas suportadas: Pacote oficial `esp32` da Espressif instalado via Gerenciador de Placas.
   * Bibliotecas necessárias (disponíveis no Library Manager):
     * `PubSubClient` (por Nick O'Leary)
     * `Adafruit AHTX0` e `Adafruit BusIO`
     * `Adafruit PWM Servo Driver Library`
2. **ESPHome Dashboard** (local ou como complemento no Home Assistant).
3. **EasyEDA** (versão Standard online ou desktop) para visualização e edição das placas de circuito impresso.

---

## ⚡ Mapeamento Rápido de Pinagens (Pinout Cheat-Sheet)

### Volume 1 (Domótica em Caixa 4x2)
| Função | Pino no ESP32 | Observação de Engenharia |
| :--- | :---: | :--- |
| **Relé (Carga)** | `GPIO 23` | Lógica *Active LOW*. Evita pinos oscilantes de boot. |
| **Interruptor Físico** | `GPIO 18` | Requer pull-up rígido externo (1kΩ) e filtro RC. |
| **Radar mmWave (RX/TX)**| `GPIO 16 / 17` | Comunicação UART2 nativa a 256.000 bps. |
| **Barramento I2C (SDA/SCL)** | `GPIO 21 / 22` | Sensor AHT20/BMP280 com resistores de pull-up. |

### Volume 2 (Alimentação e Controle de Robô)
| Função | Pino no ESP32 | Observação de Engenharia |
| :--- | :---: | :--- |
| **Driver Motores (PWMA)**| `GPIO 19` | Saída LEDC configurada a 20 kHz (inaudível). |
| **Driver Motores (AIN1/2)**| `GPIO 18 / 5` | Seleção de sentido de rotação e frenagem. |
| **Driver Motores (STBY)**| `GPIO 23` | Nível BAIXO desativa saídas físicas (Fail-Safe). |
| **Telemetria Bateria (ADC)**| `GPIO 35` | Entrada analógica pura via divisor 100kΩ/47kΩ com grampo. |
| **Servos (SDA/SCL PCA9685)**| `GPIO 21 / 22` | Barramento de dados para geração de PWM autônomo. |
| **Segurança Servos (OE)** | `GPIO 17` | Bloqueia pulsos de servo no boot para evitar trancos. |

---

## 📦 Como Fabricar as Placas de Circuito Impresso (PCB)

Dentro de cada pasta `hardware/gerber_pcb/` há um arquivo compactado `.zip` pronto para envio à fábrica:

1. Baixe o arquivo `.zip` correspondente ao projeto.
2. Acesse a fábrica de sua preferência (ex: JLCPCB, PCBWay).
3. Faça o upload do `.zip` na tela de cotação rápida.
4. Parâmetros recomendados para ambos os projetos:
   * **Layers:** 2 Camadas (*2-Layer*).
   * **Espessura:** 1.6 mm.
   * **Espessura do Cobre:** 1 oz ($35\ \mu\text{m}$) para o Volume 1; **1 oz ou 2 oz** para a PDB do Volume 2.
   * **Acabamento:** HASL com chumbo ou Lead-Free HASL.

---

## 📄 Licença

O código-fonte e os esquemáticos deste repositório estão licenciados sob a **Licença MIT** — você tem liberdade total para utilizar, modificar e incorporar os circuitos e algoritmos em seus próprios projetos comerciais ou acadêmicos. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.
