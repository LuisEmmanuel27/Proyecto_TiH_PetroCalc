# 1. Comprensión de las ecuaciones

Antes de cualquier cosa lo primero es entender la serie de ecuaciones que fueron solicitadas en los requisitos del proyecto, ya que con eso podremos saber con certeza como podremos desarrollar la aplicación, lo que el usuario debe proporcionar y lo que la aplicación debe tener ya lista para funcionar.

## Compresibilidad del Aceite

### Vazquez-Beggs

$$
C_o = \frac{-1433 + 5R_{s} + 17.2T - 1180\gamma_g + 12.61\gamma_o}{10^5p}
$$

Dondé:

- `Co` es la **compresibilidad del petróleo**
- `Rs` representa la **relación gas-aceite** en el punto de burbuja. (min 0.1, max 20000)
- `T` es la **temperatura.** (°F - min 33, max 3000)
- `γg` es la **gravedad específica del gas** (min 0.55, max 2)
- `γo` es la **gravedad del aceite** (min 5, max 100)
- `p` es la **presión** en psi. (min 0, max 30000)

## Factor de volumen del aceite

### Standing

$$
B_{o} = 0.9759 + 1.2\times10^-4 [R_s(\frac{\gamma_g}{\gamma_o})^{0.5}+1.25(T-460)]^{1.2}
$$

Dondé:

- `Bo` es el **Factor de volumen del aceite, Standing** 
- `Rs` es la **Relación gas disuelto - aceite** (100 a 2500 scf/STB -pies cúbicos estándar por barril de stock tank)
- `γg` es la **gravedad específica del gas** (0.55 a 1.7)
- `γo` es la **gravedad del aceite** (min 5, max 100)
- `T` es la **temperatura** (100 a 350 °F)

### Vazquez & Beggs

$$
B_o = 1 + C_1R_s + (T-520)(\frac{API}{\gamma_{gs}})[C_2 + C_3R_s]
$$

Dondé:

- `Bo` es el **Factor de volumen del aceite, Vazquez & Beggs**
- `Rs` es la **Relación gas disuelto - aceite** (100 a 2500 scf/STB -pies cúbicos estándar por barril de stock tank)
- `γgs` es la **gravedad del gas a la presión de referencia del separador**

`γgs` esta dada en este caso por:

$$
\gamma_{gs} = \gamma_g[1+5.912(10^{-5})(API)(T_{sep}-460)\log(\frac{\rho_{sep}}{114.7})]
$$

Dondé:

- `Tsep` es la **temperatura de separación**
- `Psep` es la **presión de separación**
- `γg` es la **gravedad del gas en las condiciones reales del separador de Psep y Tsep**

Además:

| COEFFICIENT | API ≤ 30      | API > 30     |
| ----------- | ------------- | ------------ |
| C1          | 4.677 × 10⁻⁴  | 4.670 × 10⁻⁴ |
| C2          | 1.751 × 10⁻⁵  | 1.100 × 10⁻⁵ |
| C3          | -1.811 × 10⁻⁸ | 1.337 × 10⁻⁹ |

### Glaso

$$
B_o = 1.0 + 10^A
$$

Dondé:

$$
A = -6.58511 + 2.91329\log(F) - 0.27683(\log(F))^2
$$

Siendo:

$$
F = R_s(\frac{\gamma_{g}}{\gamma_o})^{0.526} + 0.968T
$$

Dondé:

- `Bo` es el **Factor de volumen del aceite, Glaso**
- `γg` es la **gravedad específica del gas** (0.55 a 1.7)
- `γo` es la **gravedad del aceite** (min 5, max 100)
- `T` es la **temperatura**
- `Rs` es la **Relación gas disuelto - aceite** (100 a 2500 scf/STB - pies cúbicos estándar por barril de stock tank)

### Petrosky

$$
B_o = 1.0113 + 7.2046(10^{-5})A
$$

Siendo:

$$
A = [R_s^{0.3738}(\frac{\gamma_g^{0.2914}}{\gamma_g^{0.6265}}) + 0.24626(T - 460)^{0.5371}]^{3.0936}
$$

Dondé:

- `Bo` es el **Factor de volumen del aceite, Petrosky**
- `γg` es la **gravedad específica del gas** (0.55 a 1.7)
- `γo` es la **gravedad del aceite** (min 5, max 100)
- `Rs` es la **Relación gas disuelto - aceite** (100 a 2500 scf/STB - pies cúbicos estándar por barril de stock tank)
- `T` es la **temperatura**

### Kartoadmojo

$$
B_o = 0.98496 + 0.0001F^{1.5}
$$

Siendo:

$$
F = R_{s}^{0.755}\gamma_g^{0.25}\gamma_o^{-1.5}+0.45(T-460)
$$

Dondé:

- `Bo` es el **Factor de volumen del aceite, Kartoadmojo**
- `Rs` es la **Relación gas disuelto - aceite** (100 a 2500 scf/STB - pies cúbicos estándar por barril de stock tank)
- `γg` es la **gravedad específica del gas** (0.55 a 1.7)
- `γo` es la **gravedad del aceite** (min 5, max 100)
- `T` es la **temperatura**

## Presión de burbuja/saturación y Relación de solubilidad

### Standing

**Presión de burbuja**

$$
P_b = 18.2[(\frac{R_s}{\gamma_g})^{0.83}(10)^a-1.4]
$$

$$
a = 0.00091(T - 460) - 0.0125API
$$

**Relación de solubilidad**

$$
R_s = \gamma_g[(\frac{\rho}{18.2}+1.4)10^x]^{1.2048}
$$

$$
x = 0.0125API - 0.00091(T-460)
$$

Dondé:

- `Pb` es la **presión del punto de burbuja, psia**
- `Rs` representa la **relación gas-aceite** en el punto de burbuja
- `T` es la **Temperatura**
- `p` es la **presion, psia**
- `γg` es **la gravedad específica del gas**

### Vazquez & Beggs

**Presión de burbuja**

$$
P_b = [(\frac{C_1R_s}{\gamma_{gs}})(10^a)]^{C_2}
$$

$$
a = \frac{-C_3API}{T}
$$

| COEFFICIENT | API ≤ 30 | API > 30 |
| ----------- | -------- | -------- |
| C1          | 27.624   | 56.18    |
| C2          | 0.914328 | 0.84246  |
| C3          | 11.172   | 10.393   |

**Relación de solubilidad**

$$
R_s = C_1\gamma_{gs}p^{C_2}e^{[C_3(\frac{API}{T})]}
$$

| COEFFICIENT | API ≤ 30 | API > 30 |
| ----------- | -------- | -------- |
| C1          | 0.0362   | 0.0178   |
| C2          | 1.0937   | 1.1870   |
| C3          | 25.7240  | 23.931   |

$$
\gamma_{gs} = \gamma_g[1+5.912(10^{-5})(API)(T_{sep}-460)\log(\frac{\rho_{sep}}{114.7})]
$$

Dondé:

- `Tsep` es la **temperatura de separación**
- `Psep` es la **presión de separación** 
- `γgs` es la **gravedad del gas a la presión de referencia del separador**
- `γg` es la **gravedad del gas en las condiciones reales del separador de Psep y Tsep**

### Lasater

**Presión de burbuja**

$$
P_b = \frac{p_f(T+460)}{\gamma_{gd}}
$$

$$
p_f = 5.043y_g^3 + 3.10526y_g^2 + 1.36226y_g + 0.119118
$$

$$
y_g = \frac{(\frac{R_s}{379.3})}{[\frac{R_s}{379.3}+\frac{350\gamma_o}{M_o}]}
$$

Sí

$$
15<=API<=40, M_o = \frac{63.506-API}{0.0996} 
$$

$$
40<API<=55, M_o = (\frac{1048.33}{API})^{1.6736} 
$$

**Relación de solubilidad**

$$
R_s = \frac{132.755\gamma_o\gamma_g}{M_o(1-\gamma_g)}
$$

Dondé:

$$
p_f = \frac{p\gamma_{gd}}{T + 460}
$$

Sí 

$$p_f <= 7$$

$$
y_{gd} = 419.545\times10^{-5}p_f^3 - 591.428\times10^{-4}p_f^2 + 334.519\times10^-3p_f + 169.879\times10^{-4}
$$

Sí

$$p_f > 7, y_g = 0.88$$

### Glaso

**Presión de burbuja**

$$
\log(P_b) = 1.7669 + 1.7447 \log(P_b^*) - 0.30218[P_b^*]^2
$$

$$
P_b^* = (\frac{R_s}{\gamma_g})^a(t)^b(API)^c
$$

$$a = 0.816$$
$$b = 0.172$$
$$a = -0.989$$

en caso de aceite volátil

$$b = 0.130$$

Dondé

- `Rs` es la **solubilidad del gas, scf/STB**
- `t` es el **sistema de temperatura**
- `γg` es la **gravedad específica promedio de los gases totales de la superficie**

**Relación de solubilidad**

$$
R_s = \gamma_g[(\frac{API^{0.989}}{(T-460)^{0.172}})(P_b^*)]^{1.2255}
$$

$$
P_b^* = 10^x
$$

$$
x = 2.8899 - [14.1811 - 3.3093\log(\rho)]^{0.5}
$$

- `p` es la **presion, psia**

### Kartoadmojo and Schmidt

**Relación de solubilidad**

Sí:

$$API <= 30$$

Entonces:

$$
R_s = 0.05958\gamma_g^{0.7972}\rho^{1.0014}10^{13.1405}\gamma_oAPI(T+459.67)
$$

Sí:

$$API > 30$$

Entonces:

$$
R_s = 0.03150\gamma_g^{0.7587}\rho^{1.0937}10^{11.2895}\gamma_oAPI(T+459.67)
$$

## Viscosidad del aceite muerto, saturado y bajosaturado

### Vazquez & Beggs (solo bajosaturado, en teoría)

**Viscosidad del aceite muerto**

_Es el mismo que de Beggs y Robinson_

**Viscosidad del aceite saturado**

_Es el mismo que de Beggs y Robinson_

**Viscosidad del aceite bajosaturado**

$$
\mu_o = \mu_{ob}(\frac{p}{p_b})^m
$$

Dondé:

$$
m = C_1p^{C_2}exp(C_3+C_4p)
$$

$$C_1 = 2.6$$
$$C_2 = 1.187$$
$$C_3 = -11.513$$
$$C_4 = -8.98\times10^{-5}$$

Dondé:

- `P` Es la presión del sistema o del fluido. En este caso, se refiere a la presión actual del aceite.
- `Pb` Es la presión de burbujeo o presión de saturación. Esta es la presión a la cual empiezan a formarse las primeras burbujas de gas en el aceite cuando este se descomprime o se calienta.

### Kartoadmojo

**Viscosidad del aceite muerto**

$$
\mu_{od} = A \cdot B
$$

Siendo:

$$
A = 1.6\times10^9T^{-2.8177}
$$

$$
B = [\log(API)]^{5.7526\log(T)-26.9718}
$$

**Viscosidad del aceite saturado**

$$
\mu_{ob} = -0.06821 + 0.9824f + 0.000403f^2
$$

Siendo:

$$
f = [0.2001 + 0.8428(10^{-0.000845}R_s)](x)
$$

Dondé

$$
x = \mu_{od}^{(0.43+0.5165y)}
$$

$$
y = 10^{-0.00081R_s}
$$

**Viscosidad del aceite bajosaturado**

$$
\mu_o = 1.00081\mu_{ob} + 0.001127(p-p_b)(-0.006517\mu_{ob}^{1.19279}+0.038\mu_{ob}^{1.59})
$$

Dondé:

- `P` Representa la presión en el sistema.
- `Pb` Representa la presión de burbujeo, que es la presión a la cual el gas comienza a liberarse del aceite.

### De Guetto (saturado y bajosaturado)

**Viscosidad del aceite muerto**

_Es el mismo que de Beggs y Robinson_

**Viscosidad del aceite saturado**

_Es el mismo que de Beggs y Robinson_

**Viscosidad del aceite bajosaturado**

$$
\mu_o = \mu_{ob} + (\frac{p}{p_b-1})(\frac{10^{-2.488}\mu_{od}^{0.9036}p^{0.6151}}{10^{0.0197API}})
$$

### Petrosky

**Viscosidad del aceite muerto**

$$
\mu_{od} = A \cdot B
$$

Siendo:

$$
A = 2.3511\times10^7T^{-2.10255}
$$

$$
B = [\log(API)]^{4.59388\log(T)-22.82792}
$$

### Beggs y Robinson (muerto y saturado)

**Viscosidad del aceite muerto**

$$
\mu_{od} = 10^x-1
$$

Dondé:

$$
x = 10^{3.0324-0.02023API}\cdot T^{-1.163}
$$

**Viscosidad del aceite saturado**

$$
\mu_{ob} = a \cdot (\mu_{od})^b
$$

Dondé:

$$
a = 10.715(R_s+100)^{-0.515}
$$

$$
b = 5.44(R_s+150)^{-0.338}
$$