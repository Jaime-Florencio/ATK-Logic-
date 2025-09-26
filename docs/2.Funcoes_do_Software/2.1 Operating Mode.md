# 2.1 Operating Mode

O **ATK-Logic DL16** suporta dois modos principais de operação, configuráveis em:
`Device Configuration -> Options -> Mode`.

![Operating Mode Options](../assets/2.1_operating_mode.png)

---

## 🔹 Buffer Mode

- **Descrição:**
  - Os dados coletados são **armazenados primeiro na memória interna** do dispositivo.
  - Após atingir a profundidade de amostragem definida, os dados são enviados para o software.
  - Permite atingir taxas de amostragem **mais altas** que o modo Stream, pois não depende da transmissão USB em tempo real.

- **Vantagens:**
  - Maior taxa de amostragem (até 250 MHz em 16 canais no DL16).
  - Captura transientes rápidos com maior precisão.
  - Suporta compressão **RLE** para aumentar a profundidade quando o sinal tem poucas mudanças.

- **Limitações:**
  - Profundidade de amostragem limitada pela memória interna do hardware (1 Gbit no DL16).
  - Não adequado para observações de **longa duração**.

---

## 🔹 Stream Mode

- **Descrição:**
  - Os dados são transmitidos **diretamente via USB** ao computador enquanto são coletados.
  - A profundidade de captura é limitada apenas pela memória do computador.
  - Suporta decodificação de protocolos em tempo real.

- **Vantagens:**
  - Duração de captura muito maior (depende da RAM do PC).
  - Ideal para monitoramento contínuo de sinais.

- **Limitações:**
  - Taxa de amostragem reduzida (máx. 100 MHz em 3 canais no DL16).
  - Dependente da estabilidade da conexão USB.

---

## 📌 Comparação Rápida

| Modo   | Taxa de Amostragem | Profundidade | Ideal para |
|--------|-------------------|--------------|------------|
| Buffer | Alta (até 250 MHz/16ch) | Limitada pela memória interna (1 Gbit) | Eventos rápidos, transientes |
| Stream | Limitada pelo USB (até 100 MHz/3ch) | Depende da RAM do PC | Monitoramento longo, protocolos |

---

📖 *Baseado no manual ATK-Logic (Seção 5.1 Operating Mode) e considerando o modelo DL16.*
