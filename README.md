# ATK-Logic — Guia prático e anotações de uso

> Repositório para estudos, exemplos e boas práticas no uso do **ATK-Logic** (analisador lógico da ALIENTEK). Conteúdo em PT-BR, com foco didático e direto ao ponto.

## 📦 Objetivos do repo

* Centralizar **anotações** e **print screens** da interface.
* Reunir **exemplos de captura** (arquivos de sessão) e **protocolos decodificados**.
* Explicar, com linguagem simples, **taxa de amostragem**, **depth**, **trigger** e **modos de captura**.
* Deixar um **passo-a-passo** para usos comuns (UART, I²C, SPI, PWM).

---

## 🗂️ Estrutura sugerida

```
atk-logic-notes/
├── README.md               # (este arquivo)
├── docs/
│   ├── sampling.md         # taxa de amostragem, Nyquist vs prática, exemplos
│   ├── depth.md            # profundidade de memória, cálculo de janela temporal
│   ├── trigger.md          # tipos de trigger, exemplos por protocolo
│   ├── modes.md            # Buffer vs Stream, quando usar cada um
│   ├── demo-fileopen.md    # usando o Demo e abrindo arquivos salvos
│   └── troubleshooting.md  # dicas de diagnóstico
├── examples/
│   ├── uart/
│   │   ├── readme.md
│   │   └── *.atklog        # (coloque aqui arquivos de captura)
│   ├── i2c/
│   │   ├── readme.md
│   │   └── *.atklog
│   ├── spi/
│   │   ├── readme.md
│   │   └── *.atklog
│   └── pwm/
│       ├── readme.md
│       └── *.atklog
└── screenshots/
    ├── home.png
    ├── config-panel.png
    └── decode-uart.png
```

> **Dica**: se os arquivos de captura forem grandes, considere usar *Git LFS*.

---

## 🚀 Primeiros passos rápidos

1. **Conecte** o analisador lógico via USB.
2. Abra o ATK-Logic → painel direito **Configuration**.
3. **Channel**: selecione os canais que vai medir.
4. **Sampling**:

   * *Param*: escolha **taxa de amostragem** (p.ex. 20 MHz) e **janela** (p.ex. 500 ms).
   * *Thold*: ajuste o nível lógico (p.ex. 3.3V CMOS).
   * *Depth*: veja quantas amostras por canal estão disponíveis.
5. **Trigger**: defina a condição (p.ex. borda de subida em CH0 ou start I²C).
6. **Options → Mode**:

   * **Buffer** (bloco fixo de dados) ou **Stream** (visualização contínua, dependente da banda USB).
7. **Run/Capture** e salve o arquivo em `examples/`.

---

## 📚 Glossário essencial (sem jargão)

### Taxa de amostragem (Sampling rate)

Quantas “fotos” por segundo o ATK-Logic tira do seu sinal (ex.: 20 MHz = 20 milhões de amostras/s).

* **Regra teórica (Nyquist)**: ≥ 2× a maior frequência do sinal.
* **Regra prática para digitais**: 5–10× a frequência da onda **ou** resolução desejada na borda.

### Depth (profundidade de memória)

Quantas amostras por canal cabem no buffer. Junto com a taxa de amostragem, define **quanto tempo** de captura você consegue gravar.

> Ex.: 10 MSa/ch a 20 MHz ⇒ 0,5 s de janela por canal.

### Trigger

Condição que dispara/inicia a captura (borda ↑/↓, nível, padrão, evento de protocolo). Ajuda a pegar **o momento certo** (ex.: byte específico no UART).

### Modes — Buffer vs Stream

* **Buffer**: grava um **bloco fechado** de dados com alta fidelidade; ideal para analisar uma sequência completa de pacotes.
* **Stream**: envia dados **em tempo real** para o PC; útil para monitorar atividade contínua. Pode reduzir taxa efetiva quando a banda USB é o gargalo.

### Demo & File open

* **Demo**: gera sinais fictícios; treine a navegação, zoom, medidas e trigger **sem hardware**.
* **File open**: reabre capturas salvas para estudo offline.

---

## 🔧 Receitas rápidas (cookbook)

### UART (TTL 3.3V)

1. **Sampling**: 10–20× a *baud rate* (p.ex. 1–2 MHz para 115200 bps) — margem confortável para bordas.
2. **Channels**: RX (e TX, se disponível).
3. **Trigger**: borda de descida (start bit) ou decodificação de byte específico.
4. **Decode**: configure baud, 8N1 etc., e ative o decodificador UART.

### I²C (100 k / 400 k / 1 M)

1. **Sampling**: ≥ 10× a frequência (ex.: 4–10 MHz em 400 kHz).
2. **Channels**: SDA e SCL.
3. **Trigger**: start condition; opcional: endereço do slave.
4. **Decode**: habilite I²C, verifique *pull-ups* e níveis.

### SPI (1–20 MHz típ.)

1. **Sampling**: ≥ 5–10× da frequência de clock SPI.
2. **Channels**: SCK, MOSI, MISO, CS.
3. **Trigger**: borda de CS ou padrão de comando.
4. **Decode**: selecione modo (CPOL/CPHA), bit order.

### PWM (medir duty e período)

1. **Sampling**: escolha para ter ≥ 10 pontos por período.
2. **Trigger**: borda de subida.
3. **Measure**: use cursores para largura de pulso, período e duty.

> **Observação**: As recomendações acima visam **visualização e medição** estáveis (bordas e tempos). Se o objetivo for apenas detecção de evento, Nyquist (2×) pode bastar; para metrologia de borda, use 5–10×.

---

## 🧮 Regras úteis de bolso

* **Resolução temporal** ≈ 1 / (taxa de amostragem). Ex.: 20 MHz ⇒ 50 ns.
* **Janela de captura** ≈ depth / taxa de amostragem.
* **Pontos por período** ≈ taxa de amostragem / frequência do sinal.

---

## 🐞 Troubleshooting básico

* **Nada aparece**: cheque *Channel* habilitado, *Thold* correto (3.3V/5V), cabo GND comum.
* **Sinal flutuando**: adicione resistores *pull-up/down* conforme o barramento.
* **Decode errado**: verifique *baud rate* (UART), CPOL/CPHA (SPI), *pull-ups* (I²C).
* **Perda em Stream**: reduza taxa de amostragem ou troque para **Buffer**.

---

## 🛠️ Roadmap do repo

* [ ] Adicionar exemplos reais (UART/I²C/SPI/PWM) em `examples/`.
* [ ] Print screens comentados em `screenshots/`.
* [ ] Anotações detalhadas em `docs/` (sampling, depth, trigger, modes, demo/fileopen).
* [ ] Tabela "frequência recomendada de amostragem" por protocolo.

---

## 🤝 Contribuição

Sinta-se livre para abrir *issues* com dúvidas, sugestões e correções.

## 📝 Licença

Licença sob **MIT** (simples e permissiva). Veja o arquivo `LICENSE`.
