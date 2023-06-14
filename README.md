# Tensile Test Analysis

This Python notebook is used to compute mechanical properties based on a tensile test data for a metallic material

## 🔰 How does it work?

- The tensile test data is uploaded from a excel file. This file contains the load [kN] and the length of metallic piece [mm]

- The engineering stress $(\sigma)$ and strain $(\varepsilon)$ are calculated using the following equations

$$\sigma = \frac{F}{A_0}$$

$$\varepsilon = \frac{L_i - L_0}{L_0}$$

Where $F$ is the load, $A_0$ is the initial area, $L_i$ is the instantaneous length, and $L_0$ is the initial length.

- Young's Modulus is computed based on the elastic behaviour. Two methods are used for this calculation.

$$\sigma = E\varepsilon$$

  1. *Slope method*: In this method, the linear equation is used to find the value of the slope $(m)$ based on the first and last value of the elastic region.

$$ y = mx + b$$

$$m = \frac{y_2 - y_1}{x_2 - x_1} = \frac{\sigma_2 - \sigma_1}{\varepsilon_2 - \varepsilon_1}$$

  2. *Liner regression*: A linear regression is performed on the elastic region data

- The yield strength $(\sigma_Y)$ is calculated using the 0.2% offset. For this, a 3rd degree polynomial is used to fit the tensile test data. The intersection of the 3rd degree polynomial and the 0.2% offset line would be the yield point.

- The tensile strength $(\sigma_U)$ would be the maximun stress value of  of the tensile test data.

- The failure strength $(\sigma_F)$ would be the last stress value of  of the tensile test data.

- Elongation is computed with the following equation

$$EL = \left({\frac{L_f - L_0}{L_0}}\right)100$$

- Reduction in area is computed with the following equation

$$RA = \left({\frac{A_0 - A_f}{A_0}}\right)100$$
    
- Resilience is computed with the following equation

$$U_R \cong \frac{1}{2}\sigma_Y\varepsilon_Y$$

- Toughness modulus (area under the curve) is computed using three methods
1. Polyfit and polynomial integration
2. Spline interpolation and integration
3. Trapezoidal integration 
