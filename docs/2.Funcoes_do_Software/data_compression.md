# 🧮 Measure (Ferramentas de Medição)

A aba **Measure** concentra ferramentas que auxiliam na análise quantitativa dos sinais capturados.

---

## 📏 Ferramentas principais

| Ferramenta | Descrição | Como usar |
| --- | --- | --- |
| **Cursors** | Dois cursores verticais com diferença de tempo e frequência. | Arraste `A` e `B` sobre o sinal; veja Δt, 1/Δt e contagem de amostras. |
| **Timing Table** | Lista eventos (bordas e pulsos) em formato tabular. | Habilite na barra lateral; exporte CSV para análise externa. |
| **Measurements** | Métricas automáticas (duty cycle, frequência, período). | Clique em `Add Measurement` e selecione o canal. |
| **Statistics** | Resumo global de capturas longas. | Útil para detectar jitter, pulsações irregulares ou variação de duty cycle. |

---

## ⚙️ Procedimento sugerido

1. Posicione os cursores para delimitar a janela de interesse.
2. Ative as medições automáticas para acompanhar o comportamento durante a captura.
3. Utilize a tabela temporal para identificar eventos anômalos e saltar diretamente para eles.
4. Exporte os dados quando precisar documentar testes ou anexar resultados em relatórios.

---

## ✅ Boas práticas

- Combine cursores com zoom horizontal para medir tempos muito curtos com maior precisão.
- Antes de exportar, ajuste a base de tempo e o número de amostras para reduzir o tamanho do arquivo.
- Salve presets de medições para reutilizar entre diferentes projetos.

---

## 📚 Referências

- Manual ATK-Logic – capítulo **Measurement Tools**.
- Tutoriais oficiais: *“Using cursors effectively”* e *“Exporting timing tables”*.
