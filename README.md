# roberto-carlos


# 🚀 Minifoguete de 50 cm — Simulação Teórica de Trajetória e Apogeu

Modelo simplificado de física para estimativa de trajetória, dinâmica de massa variável e resistência aerodinâmica de um minifoguete de 50 cm.

---

## 📊 Parâmetros do Modelo

| Parâmetro | Símbolo | Valor | Unidade |
| :--- | :---: | :---: | :---: |
| **Massa Inicial (Com combustível)** | $m_0$ | `0.30` | kg |
| **Massa Seca (Estrutura pós-queima)** | $m_s$ | `0.15` | kg |
| **Massa de Combustível** | $m_f$ | `0.15` | kg |
| **Tempo de Queima** | $t_q$ | `1.5` | s |
| **Taxa de Perda de Massa** | $\dot{m}$ | `0.10` | kg/s |
| **Empuxo Médio do Motor** | $F$ | `12.0` | N |
| **Constante de Arrasto Aerodinâmico** | $k$ | `0.000344` | kg/m |
| **Aceleração da Gravidade** | $g$ | `9.81` | m/s² |

---

## ⚡ 1. Fase Propulsada ($0 \le t \le 1.5\text{ s}$)

Durante a queima, a massa varia linearmente com o tempo:

$$m(t) = m_0 - \dot{m} \cdot t = 0.30 - 0.10t$$

### Aceleração Média ($\bar{a}$)
$$\bar{a} \approx \frac{F - \bar{m}g}{\bar{m}} = \frac{12 - (0.225 \cdot 9.81)}{0.225} \approx \mathbf{43.55\text{ m/s}^2}$$

### Velocidade ao Fim da Queima ($v_1$)
$$v_1 \approx \mathbf{58\text{ m/s}} \quad (\approx 208.8\text{ km/h})$$

### Altura ao Fim da Queima ($h_1$)
$$h_1 \approx \frac{1}{2} \bar{a}_{efetiva} \cdot t_q^2 \approx \frac{1}{2} \cdot 38 \cdot (1.5)^2 = \mathbf{42.75\text{ m}}$$

---

## 🍃 2. Fase de Voo Livre / Inércia ($t > 1.5\text{ s}$)

Após a queima do combustível, o minifoguete prossegue apenas com sua massa seca ($m_s = 0.15\text{ kg}$).

### Ganho de Altura Adicional ($h_2$)
$$h_2 = \frac{m_s}{2k} \cdot \ln\left(1 + \frac{k \cdot v_1^2}{m_s \cdot g}\right)$$

$$h_2 = \frac{0.15}{2 \times 0.000344} \cdot \ln\left(1 + \frac{0.000344 \times 58^2}{0.15 \times 9.81}\right) \approx \mathbf{126.4\text{ m}}$$

---

## 🎯 3. Resultados Globais

```text
=====================================================
  APOGEU TOTAL (H):       169.15 metros
  TEMPO ATÉ O APOGEU:     5.1 segundos
  VELOCIDADE MÁXIMA:      58.0 m/s  (208.8 km/h)
=====================================================
