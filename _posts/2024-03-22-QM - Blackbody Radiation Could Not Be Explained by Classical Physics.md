# QM - Blackbody Radiation Could Not Be Explained by Classical Physics

1800년대 말 . . 과학자들에게 다음과 같은 사실은 당연하게 받아들여졌습니다

> Phenomena1: 금속에 열을 가하면 빛(radiation)이 나온다

> Phenomena2: 그 열이 낮은 온도면 빨간색, 높은 온도면 푸른색과 하얀색을 띈다.


과학자들이 좋아하는 것은 간단한 것입니다. (정말입니다)

과학자들은 현상을 해석할 때에 가장 간단한 모델을 통해서 생각하기를 좋아합니다.

다시 말해, 가장 이상적인 상황을 설정하여 해당 system을 완전하게 control하려 합니다.



![BlackBody](https://en.wikipedia.org/wiki/Black_body#/media/File:Black_body_realization.svg)

과학자들은 이상적인 물체(BODY)를 떠올립니다. 

소위 BLACKBODY라 부르는 물체이죠

이 흑체(blackbody)는 모든 연속적인 파장의 빛을 흡수하고 방출할 수 있습니다. (물론, 이상적으로요)


---

일련의 실험들을 통해 주파수에 따른 빛의 세기 plot을 얻을 수 있었는데요, 다음과 같습니다.

<span style="font-style: italic ; color: Orange; font=family: arial;">(plot은 변수들 간의 관계를 보여주는 diagram이나 chart, graph등을 말합니다.)</span>



```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
h = 6.62607015e-34  # Planck's constant (m^2 kg / s)
c = 2.99792458e8     # Speed of light (m/s)
kB = 1.380649e-23    # Boltzmann constant (m^2 kg / s^2 K)

# Function to calculate blackbody spectral radiance
def blackbody_radiance(wavelength, T):
    """
    Calculate blackbody spectral radiance using Planck's law.
    
    Arguments:
    - wavelength: Wavelength in meters
    - T: Temperature in Kelvin
    
    Returns:
    - Spectral radiance in W / (m^2 * m)
    """
    numerator = 2 * h * c**2 / wavelength**5
    denominator = np.exp(h * c / (wavelength * kB * T)) - 1
    return numerator / denominator

# Define range of wavelengths (in meters)
wavelengths = np.linspace(1e-9, 3e-6, 1000)  # 1 nm to 3 µm

# Define temperatures in Kelvin
temperatures = [5800, 5000, 4000, 3000]

# Plot blackbody radiation curves for each temperature
plt.figure(figsize=(10, 6))
for T in temperatures:
    radiance = blackbody_radiance(wavelengths, T)
    plt.plot(wavelengths * 1e9, radiance, label='{} K'.format(T))

plt.title('Blackbody Radiation Spectrum')
plt.xlabel('Wavelength (nm)')
plt.ylabel('Spectral Radiance (W / (m^2 * nm))')
plt.grid(True)
plt.legend()
plt.show()

```

    C:\Users\CDLC_johnh\AppData\Local\Temp\ipykernel_4452\3898778319.py:22: RuntimeWarning: overflow encountered in exp
      denominator = np.exp(h * c / (wavelength * kB * T)) - 1
    


    
![png](output_7_1.png)
    


![BlackBodyRadiation](https://en.wikipedia.org/wiki/Black-body_radiation#/media/File:Black_body.svg)

이론물리학자들은 이 그래프를 함수(주파수에 따른 빛의 세기와의 관계)로 표현하고 싶었지만, 성공적이지 못했습니다 . . .


(성공하지 못한 예를 들자면, **Rayleigh-Jeans law** 가 있습니다.)

저명하신 이론물리학자분들께서도 위와 같이 간단한 식을 표현하지 못하다니 답답합니다.


*그들이 물리법칙을 제대로 알지 못해서 BlackBody Radiation을 설명하지 못한 것일까요?*


아니요, 당시의 Classical Mechanics(고전역학)으로는 현상을 설명하는 데에 한계가 있었던 것입니다.



과학자들을 서서히 기존의 물리법칙이 만능 법칙이 아니라는 것을 느끼게 됩니다. (원래는 만능이라 생각했었거든요)

### 새로운 물리법칙이 필요함이 느껴집니다
### 양자역학의 시대가 탄생하려 꿈틀거리기 시작합니다.

***

#### c.f.  Rayleigh-Jeans law

$$ \rho_\nu\left(T \right)d\nu = \frac{8\pi k_B T}{c^3}\nu^2d\nu$$

where, $k_B$ : Boltzman Constant, $T$ : Temperature, $c$: speed of light, $\nu$: frequency


```python

```
