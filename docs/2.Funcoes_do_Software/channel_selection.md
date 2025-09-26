# 🔗 Protocols (Decodificadores)

Os **decodificadores de protocolo** transformam formas de onda em dados legíveis (bytes, palavras, pacotes). Eles aceleram a análise de comunicações seriais e paralelas.

---

## 📡 Protocolos suportados

- **UART / RS-232**: configuração de baud rate, paridade, bits de dados e stop.
- **SPI**: suporta modos 0 a 3, seleção de bit order e largura do word.
- **I²C**: identificação automática de `START`/`STOP`, ACK/NACK e endereços de 7/10 bits.
- **CAN / LIN**: destaca ID, DLC, payload e flags de erro.
- **Protocolos customizados**: crie templates com base em máquina de estados e expressões regulares de bits.

---

## ⚙️ Como configurar

1. **Abra o painel Protocols** e clique em `Add Analyzer`.
2. **Escolha o protocolo** na lista e confirme os canais envolvidos (Clock, Data, Chip Select...).
3. **Informe parâmetros** específicos (baud rate, polaridade, bit order).
4. **Defina a camada de exibição**: bolhas sobre o traço, tabela lateral ou exportação CSV.
5. **Ative filtros** para exibir apenas frames válidos, endereços específicos ou tipos de mensagem.

> 💡 É possível sincronizar múltiplos decodificadores (ex.: I²C + UART) para correlacionar comandos e respostas.

---

## 🧪 Validação e debug

- Compare os dados decodificados com logs do firmware para confirmar integridade.
- Utilize a função de busca (`Ctrl+F`) para localizar endereços, palavras-chave ou padrões hexadecimais.
- Caso a decodificação falhe, verifique se o clock está bem definido e se o sinal tem bordas limpas.

---

## 📚 Referências

- Manual ATK-Logic – capítulo **Protocol Analyzer**.
- Biblioteca de presets da comunidade (menu **Help → Download Protocol Templates**).
