# 1.1 Organização e Descrição da Telemetria

Este sistema de telemetria monitora os parâmetros críticos de segurança do veículo de lançamento em tempo real. Cada variável possui uma faixa operacional segura baseada em critérios de engenharia aeroespacial para lançamentos de foguetes de propulsão líquida.

### Variáveis Monitoradas e Faixas Seguras

**1. Temperatura Externa (°C)**
*   **Descrição:** Mede a temperatura do ambiente na plataforma de lançamento. Condições extremas de frio ou calor podem danificar os anéis de vedação (O-rings), causar condensação nos tanques criogênicos ou superaquecer componentes externos.
*   **Unidade de Medida:** Graus Celsius (°C)
*   **Faixa Segura:** Entre **-150°C e 120°C**
*   **Justificativa:** Baseado nos critérios climáticos reais que abortam lançamentos fora dessa faixa para proteger a integridade estrutural e evitar falhas.

**2. Temperatura Interna (°C)**
*   **Descrição:** Refere-se à temperatura da aviônica, compartimento de carga útil e cápsula de controle. Essencial para o funcionamento correto dos computadores de bordo, sensores e segurança da tripulação/carga.
*   **Unidade de Medida:** Graus Celsius (°C)
*   **Faixa Segura:** Entre **18°C e 24°C**
*   **Justificativa:** Faixa que garante operação ideal dos sistemas eletrônicos sensíveis e conforto térmico para tripulação/equipamentos. Temperaturas fora dessa faixa podem causar falhas em processadores e sensores.

**3. Integridade Estrutural (Booleano)**
*   **Descrição:** Valor booleano que indica se os sensores de casco, chassi e estrutura primária detectaram alguma microfissura, vibração anômala, deformação ou falha nos painéis de revestimento.
*   **Unidade de Medida:** Binário (0 ou 1)
*   **Faixa Segura:** Exatamente **1** (onde 1 = Estrutura Íntegra / 0 = Estrutura Comprometida)
*   **Justificativa:** Qualquer comprometimento estrutural detectado pelos sensores resulta em aborto imediato, pois a integridade do casco é não-negociável para suportar as forças aerodinâmicas do voo.

**4. Nível de Energia (%)**
*   **Descrição:** Carga percentual das baterias principais que alimentam os sistemas de telemetria, computadores de bordo, sistemas de separação de estágio e aviônica durante o voo até a órbita.
*   **Unidade de Medida:** Percentual (%)
*   **Faixa Segura:** Maior ou igual a **80%**
*   **Justificativa:** Margem de segurança necessária para garantir autonomia energética durante toda a fase de ascensão, incluindo reserva para contingências. Níveis abaixo de 85% comprometem a análise energética da missão.

**5. Nível de Combustível (%)**
*   **Descrição:** Percentual de preenchimento do tanque de propelente. Indica a quantidade de combustível disponível para a queima dos motores principais.
*   **Unidade de Medida:** Percentual (%)
*   **Faixa Segura:** Maior ou igual a **90%**
*   **Justificativa:** O foguete deve estar com tanques praticamente cheios (considerando margem para expansão térmica) para atingir a velocidade orbital necessária. Níveis abaixo de 95% indicam vazamento ou falha no sistema de abastecimento.

**6. Pressão do Tanque de Combustível (atm)**
*   **Descrição:** Pressão interna do tanque de propelente. A pressurização adequada garante o fluxo constante do combustível para as turbobombas dos motores durante a ignição e fase de potência máxima (Max-Q).
*   **Unidade de Medida:** Atmosferas (atm)
*   **Faixa Segura:** Entre **200 atm e 300 atm**
*   **Justificativa:** Pressão abaixo do mínimo causa cavitação nas bombas e falha dos motores. Pressão acima do máximo pode romper o tanque. Faixa baseada em sistemas de pressurização reais.

**7. Pressão do Tanque Oxidante (atm)**
*   **Descrição:** Pressão interna do tanque de oxidante. Assim como o combustível, a pressão correta do oxidante é crítica para manter a proporção estequiométrica ideal na câmara de combustão.
*   **Unidade de Medida:** Atmosferas (atm)
*   **Faixa Segura:** Entre **200 atm e 300 atm**
*   **Justificativa:** A proporção de mistura entre combustível e oxidante depende da pressurização uniforme de ambos os tanques para garantir o empuxo nominal dos motores.

**8. Status dos Sistemas (String)**
*   **Descrição:** Checagem geral do estado operacional dos módulos críticos: sistema de comunicação (telemetria/telecomando), navegação inercial (IMU/GPS), controle de atitude e controle de empuxo vetorial.
*   **Unidade de Medida:** Texto/String
*   **Faixa Segura:** Exatamente **"S"**
*   **Justificativa:** Qualquer outro status como "AVISO", "ERRO", "FALHA" ou "DEGRADADO" indica que um sistema crítico não está respondendo corretamente, resultando em aborto imediato. Todos os sistemas devem estar no estado "S" para prosseguir.

---

### Resumo das Faixas Operacionais Seguras

| Variável | Unidade | Faixa Segura |
| :--- | :--- | :--- |
| Temperatura Externa | °C | -150 ≤ valor ≤ 120 |
| Temperatura Interna | °C | 18 ≤ valor ≤ 24 |
| Integridade Estrutural | Booleano | valor = 1 |
| Nível de Energia | % | valor ≥ 80 |
| Nível de Combustível | % | valor ≥ 90 |
| Pressão Tanque Combustível | atm | 200 ≤ valor ≤ 300 |
| Pressão Tanque Oxidante | atm | 200 ≤ valor ≤ 300 |
| Status dos Sistemas | String | valor = "S" |

---

### Referências Técnicas

Este modelo de telemetria baseia-se em critérios de *launch commit criteria* (critérios de comprometimento de lançamento) da indústria aeroespacial:
- Critérios climáticos de lançamento de veículos (NASA)
- Monitoramento de pressão e sistemas aviônicos em telemetria padrão
