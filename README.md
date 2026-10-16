# Modelagem Espaço-temporal da propagação de doenças infecciosas via equações do tipo reação difusão

Modelos epidemiológicos temporais, como o amplamente utilizado SIR, assumem a hipótese simplificadora de que a população está homogeneamente distribuída no espaço. Porém, na demografia real, a densidade varia e os fluxos migratórios alteram a dinâmica de contágio. Para capturar frentes de onda e heterogeneidade territorial, permitindo uma caracterização mais confiável da infecção, transita-se para sistemas de equações diferenciais parciais (EDPs), dentre os quais apresentam-se os do tipo reação-difusão.

## Equação de Reação-difusão

Em analogia com o Princípio Físico de Conservação, estipula-se que a variação populacional em um volume de controle $V \subseteq \Omega$ combina o fluxo dispersivo $\mathbf{J}_i$, através da fronteira $\partial V$ com o termo de reação $F_i(\mathbf{u})$. Isso deduz a Equação da Continuidade para cada componente do sistema na sua forma diferencial local:

$$
\frac{\partial \mathbf{u}}{\partial t} = - \nabla \cdot \mathbf{J} + \mathbf{F}(\mathbf{u}).
$$

Para modelar o transporte puramente dispersivo e desordenado dos indivíduos em $V$, a Primeira Lei de Fick postula que o fluxo populacional orientado $\mathbf{J}_i$ é diretamente proporcional ao gradiente da sua própria densidade,

$$
\mathbf{J}_i = -D_i \nabla u_i,
$$

e, com base nisso, uma equação do tipo reação-difusão é expressa por

$$
\frac{\partial \mathbf{u}}{\partial t} = \mathbf{D} \Delta \mathbf{u} + \mathbf{F}(\mathbf{u}), \qquad \nabla u_i \cdot \mathbf{n} = 0 \text{ em } \partial\Omega
$$

em que $\mathbf{D} = \text{diag}(D_1, \dots, D_n)$ representa a mobilidade, $\mathbf{F}(\mathbf{u})$ reflete as taxas epidemiológicas e as condições de contorno garantem o isolamento da comunidade e conservação da massa total populacional.

## Instabilidade de Turing

Apesar do caráter dissipativo do Laplaciano, a combinação entre reação e difusão pode desestabilizar um equilíbrio estacionário $(\mathbf{u}^*)$ que era estável no sistema puramente temporal, provocando padrões de espalhamento não uniforme. As condições analíticas para ocorrência de tal fenômeno são:

- Estabilidade sem difusão ($\mathbf{D} = 0$): se $\mathbf{J}$ é a matriz jacobiana do sistema, deve cumprir $\mathrm{tr}(\mathbf{J}) < 0$ e $\det(\mathbf{J}) > 0$;
- Instabilidade com difusão ($\mathbf{D} > 0$): seja $k$ o número de onda espacial, requer obrigatoriamente que $\det(\mathbf{J}) < 0$ para algum $k^2 > 0$, exigindo assimetria de mobilidade ($D_i \neq D_j$) ou mecanismos ativos de dispersão.

## Coeficiente de Difusão Cruzada

Uma limitação fundamental da difusão simples é considerar que a dispersão ocorre exclusivamente em resposta ao gradiente da própria população, o que não reflete o comportamento real em epidemiologia, onde a resposta populacional pauta-se pela evitação espacial ativa: ao perceberem a densidade de infectados em dada região, os suscetíveis deslocam-se na direção oposta para mitigar o risco de contágio.

Para suprimir essa limitação, estende-se o fluxo dispersivo de suscetíveis adicionando um termo dispersivo direcionado pelo gradiente de infectados ($-D \nabla I$):

$$
\mathbf{J}_S = -D_S \nabla S - D \nabla I
$$

em que $D$ representa o coeficiente de difusão cruzada, que quantifica a intensidade da repulsão comportamental.
