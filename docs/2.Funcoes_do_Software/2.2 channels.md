# 🧵 Channels (Canais de Aquisição)

Os **canais** são as linhas físicas de entrada do analisador lógico. A forma como são configurados impacta diretamente a clareza da captura e a interpretação dos sinais.

---

## 🧭 Organização e nomenclatura

- **Nomeie os canais** de acordo com a função do sinal (`CLK`, `MISO`, `CS`, etc.).
- Reordene as linhas para agrupar sinais relacionados (ex.: todos os sinais SPI lado a lado).
- Utilize cores diferentes para canais críticos e facilite a leitura do diagrama temporal.

> 💡 Clique com o botão direito sobre o rótulo do canal para renomear, reordenar ou alterar a cor rapidamente.

---

## ⚙️ Configurações por canal

1. **Threshold lógico**: escolha o nível de tensão que separa `0` de `1` (ex.: 1,8 V, 3,3 V, 5 V).
2. **Inversão de fase**: ative quando o circuito utiliza lógica invertida (ativo em nível baixo).
3. **Filtros de glitch**: ignore pulsos inferiores a um tempo mínimo configurado para reduzir ruído.
4. **Grupos de canais**: combine linhas que representam barramentos paralelos e visualize valores hexadecimais.

---

## 📈 Boas práticas

- Ajuste o threshold para corresponder ao domínio lógico do circuito analisado.
- Desative canais que não estão sendo utilizados para economizar largura de banda e melhorar a visualização.
- Use labels consistentes com os esquemas elétricos do projeto para facilitar o trabalho em equipe.
- Para barramentos paralelos, configure a ordem bit a bit (MSB → LSB) e verifique se o alinhamento com os dados recebidos está correto.

---

## 📚 Referências

- Manual ATK-Logic – seção de **Channel Settings**.
- Vídeos de demonstração oficiais – playlist *"Channel Management"*.
