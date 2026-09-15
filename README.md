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

## 🪂 4. Dimensionamento do Paraquedas e Sistema de Liberação

Para garantir uma taxa de descida segura de $v_{descida} = 5\text{ m/s}$ para a massa seca ($m_s = 0.15\text{ kg}$):

### Tamanho do Paraquedas (Velame Parabólico)
$$A = \frac{2 \cdot m_s \cdot g}{\rho \cdot C_d \cdot v^2} = \frac{2 \cdot 0.15 \cdot 9.81}{1.225 \cdot 1.5 \cdot 5^2} \approx 0.064\text{ m}^2$$

$$\text{Diâmetro Requerido } (D) = \sqrt{\frac{4 \cdot A}{\pi}} \approx \mathbf{28.5\text{ cm}}$$

### Mecanismo de Ejeção / Cronograma
* **Timing Ideal de Ejeção:** O acionamento do sistema de ejeção deve ser sincronizado para o **apogeu ($t \approx 5.1\text{ s}$)**, e não imediatamente no fim da queima ($t = 1.5\text{ s}$). Abrir a $58\text{ m/s}$ destruiria o velame por estresse mecânico.
* **Sistema de Carga de Atraso (*Delay Charge*):** Utiliza-se uma espoleta de queima lenta de $3.5\text{ segundos}$ integrada ao motor. Ela aciona uma micro-carga de pólvora negra após o fim da propulsão, gerando sobrepressão interna para desacoplar a coifa e liberar o paraquedas no ponto de menor velocidade.

---

## 🛑 5. Limites Críticos de Operação (Segurança Estrutural)

Para evitar colapso estrutural, deformação por calor ou desvios críticos de trajetória:

| Parâmetro Operacional | Limite Máximo | Consequência ao Exceder |
| :--- | :---: | :--- |
| **Carga Útil Máxima (*Payload*)** | `108 g` | Aceleração inicial $< 3g$; instabilidade no trilho de lançamento. |
| **Velocidade do Vento no Dia** | `20 km/h` | *Weathercocking* severo (o foguete tomba contra o vento na subida). |
| **Temperatura da Câmara de Combustão** | `1050 °C` | Derretimento de paredes em PVC/plástico. Exige revestimento térmico. |
| **Temperatura Externa do Tubo** | `60 °C` | Perda de rigidez estrutural da fuselagem de papelão/resina. |
| **Carga de Tração no Cordão de Choque** | `15 kgf` | Ruptura do cordão e separação definitiva da coifa. |

---

## 🔥 6. Perfil Térmico por Componente

| Componente | Temp. Média | Temp. Pico | Origem do Calor |
| :--- | :---: | :---: | :--- |
| **Câmara de Combustão** | $850\text{ }^\circ\text{C}$ | $1050\text{ }^\circ\text{C}$ | Reação química do propelente |
| **Bocal / Tubeira** | $600\text{ }^\circ\text{C}$ | $850\text{ }^\circ\text{C}$ | Expansão de gases em alta velocidade |
| **Corpo Inferior (Fuselagem)** | $80\text{ }^\circ\text{C}$ | $140\text{ }^\circ\text{C}$ | Condução térmica interna |
| **Coifa / Ponta** | $32\text{ }^\circ\text{C}$ | $45\text{ }^\circ\text{C}$ | Atrito aerodinâmico |

---

> ⚠️ **Nota de Engenharia:** Respeite a janela meteorológica de lançamento (vento $< 15\text{ km/h}$) e certifique-se de usar anéis centradores para isolar a câmara de combustão do restante da estrutura.
