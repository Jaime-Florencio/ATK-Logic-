# ⚡ PWM Analyzer

O analisador de **PWM (Pulse Width Modulation)** ajuda a medir rapidamente ciclo ativo, frequência e estabilidade de sinais modulados em largura de pulso.

---

## 📌 Quando utilizar

- Avaliação de drivers de motores e dimmers de LED.
- Testes em conversores DC/DC com controle PWM.
- Medição de largura de pulso em controladores digitais (MCUs, FPGAs).

---

## ⚙️ Configuração

1. **Selecione o canal** que contém o sinal PWM.
2. Defina o **nível lógico** apropriado (threshold) para garantir detecção precisa das bordas.
3. Ajuste a opção **Averaging** para suavizar variações de duty cycle.
4. Habilite **histograma de duty cycle** para visualizar distribuição durante longas capturas.

---

## 🔎 Métricas apresentadas

- **Frequência** (Hz)
- **Período** (ns)
- **Duty Cycle** (%)
- **Tempo em nível alto / baixo**
- **Jitter de período** (desvio padrão)

> 💡 Combine o analisador PWM com cursores para medir intervalos específicos dentro de uma captura longa.

---

## ✅ Boas práticas

- Use taxas de amostragem altas (≥ 10× frequência PWM) para capturar detalhes das bordas.
- Ative filtros de glitch quando houver ruído devido a comutação de potência.
- Documente as medições exportando relatórios em CSV ou imagens do traço.

---

## 📚 Referências

- Manual ATK-Logic – seção **PWM Analysis**.
- Aplicações de engenharia – notas de aplicação ALIENTEK sobre controle de motores.
