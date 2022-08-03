# Trabalho de Métodos Matemáticos


## Bibliotecas importadas

```.py 

import math
from math import exp
import matplotlib.pyplot as plt
import numpy as np

```

## Questão 1

### a) Aproximando a função F(x) por seus polinômios de Taylor em torno de 25

#### Formula para os polinômios de Taylor

![](https://i.imgur.com/8jR5Wbc.png)


#### Código usado:

```.py
// Iniciando a F(x)
x = np.arange(0,50,0.1)
Funcao = np.sqrt(x)
```

```.py
// Aproximando pelo polinômio de grau 1
polinomio_grau1 = [5 + (x-25)/10 for x in x]

fig1, imagem1 = plt.subplots(figsize = (10,5))
imagem1.plot (x,Funcao)
imagem1.plot (x,polinomio_grau1)

imagem1.set_xlim([0,50])
imagem1.set_ylim([0,10])

imagem1.legend(['Função','Aproximação_polinomial'],fontsize=10)

plt.grid()

plt.show

```
#### Gráfico da aproximação pelo polinômio de grau 1
![](https://i.imgur.com/kGu2k2z.png)

```.py
// Aproximando pelo polinômio de grau 2
polinomio_grau2 = [5 + (x-25)/10 - ((x-25)**2)/1000 for x in x]

fig2, imagem2 = plt.subplots(figsize = (10,5))
imagem2.plot (x,Funcao)
imagem2.plot (x,polinomio_grau2)

imagem2.set_xlim([0,50])
imagem2.set_ylim([0,10])

imagem2.legend(['Função','Aproximação_polinomial'],fontsize=10)

plt.grid()

plt.show
```
#### Gráfico da aproximação pelo polinômio de grau 2
![](https://i.imgur.com/SoPJEDu.png)

```.py
// Aproximando pelo polinômio de grau 3
polinomio_grau3 = [5 + (1/10)*(x-25) - (1/1000)*((x-25)**2) + (1/50000)*((x-25)**3) for x in x]

fig3, imagem3 = plt.subplots(figsize = (10,5))
imagem3.plot (x,Funcao)
imagem3.plot (x,polinomio_grau3)

imagem3.set_xlim([0,50])
imagem3.set_ylim([0,10])

imagem3.legend(['Função','Aproximação_polinomial'],fontsize=10)

plt.grid()

plt.show
```
#### Gráfico da aproximação pelo polinômio de grau 3
![](https://i.imgur.com/gjNLgWS.png)

```.py
// Aproximando pelo polinômio de grau 4
polinomio_grau4 = [5 + (1/10)*(x-25) - (1/1000)*((x-25)**2) + (1/50000)*((x-25)**3) - (1/2000000)*((x-25)**4) for x in x]

fig4, imagem4 = plt.subplots(figsize = (10,5))
imagem4.plot (x,Funcao)
imagem4.plot (x,polinomio_grau4)

imagem4.set_xlim([0,50])
imagem4.set_ylim([0,10])

imagem4.legend(['Função','Aproximação_polinomial'],fontsize=10)

plt.grid()

plt.show
```
#### Gráfico da aproximação pelo polinômio de grau 4
![](https://i.imgur.com/yt9B5tq.png)

#### Conclusão:

É possivel ver que a medida que o grau dos polinômios de Taylor cresce, o gráfico do polinômio se aproxima cada vez mais do gráfico da função no ponto em questão (x = a = 25)


### b)Estimando a exatidão da aproximação da função F(x) pelo seu polinômio de Taylor de grau 4

#### Formula usada:

![](https://i.imgur.com/CvQ7TlP.png)

#### Código:
```.py
x2 = np.arange(25,26,0.05)

print ("Valores de x:")
print(x2)

Resto_polinomio_grau4 = [((105/3840)*((x2-25)**5))/(x2**(9/2)) for x2 in  x2]

print("Valores do resto de acordo com x :")
print(Resto_polinomio_grau4)

fig5, imagem5 = plt.subplots(figsize = (10,5))
imagem5.plot (x2,Resto_polinomio_grau4)

imagem5.set_xlim([25,26])
imagem5.set_ylim([-1,1])

imagem5.legend(['Resto de grau 4 com (25 < x < 26)'],fontsize=10)

plt.grid()

plt.show
```
#### Gráfico

![](https://i.imgur.com/qXCuZc3.png)

#### Conclusão

Considerando a soma parcial da função F(x) em torno de 25 indo até o polinômio de grau 4, o resto da mesma se torna muito pequeno no intervalo de 25<= x <=26 e pode ser considerado desprezível. Dessa forma, pode se dizer que o polinômio de Taylor de grau 4 da função é uma boa aproximação para a função em pontos próximos de x = 25 

## Questão 2


### a) Encontrando expressões para aproximação linear e quadrática da função P(t)

![](https://i.imgur.com/fgSARxl.png)


### b) Gráfico da função e seus polinômios de grau 1 e 2

##### Código:
```.py
t = np.arange(-250,1000,1)
Funcao2 = ((2.7)/((10)**8)) * (np.exp(0.0043*(t-20)))

aproximacao_Linear = [((2.7)/((10)**8)) + ((2.7)/((10)**8))*0.0043*(i-20) for i in t]
aproximacao_Quadratica = [((2.7)/((10)**8)) + ((2.7)/((10)**8))*0.0043*(i-20) + (1/2)*((2.7)/((10)**8))*(0.0043**2)*((i-20)**2) for i in t]

fig6, img = plt.subplots(figsize = (10,10))
img.plot (t,Funcao2)
img.plot (t,aproximacao_Linear)
img.plot (t,aproximacao_Quadratica)


limiteY = 200*(10**(-8))

img.set_xlim([-200,1010])
img.set_ylim([-limiteY,limiteY])

img.legend(['Função','aproximacao_linear','aproximacao_quadratica'],fontsize=10)

plt.grid()
plt.show()

fig7, img2 = plt.subplots(figsize = (10,10))
img2.plot (t,Funcao2)
img2.plot (t,aproximacao_Linear)
img2.plot (t,aproximacao_Quadratica)


limiteY = 200*(10**(-8))

img2.set_xlim([-250,250])
img2.set_ylim([-limiteY,limiteY])

img2.legend(['Função','aproximacao_linear','aproximacao_quadratica'],fontsize=10)

plt.grid()
plt.show()
```
#### Gráfico
![](https://i.imgur.com/gUhF43A.png)
#### Gráfico aproximando mais do ponto t= 20
![](https://i.imgur.com/EMFD0V1.png)



### c) Determinar a faixa de valores de t nos quais a aproximação fique em uma faixa de 1% do valor da função

#### Código

Essa função foi feita para descobrirmos os valores de t no limite das condição desejadas. Com a resposta do código, podemos inferir que t esta dentro do intervalo [-11.4,54.5] considerando uma casa decimal.
```.py
a = []

for i in t:
    Funcao3 = ((2.7)/((10)**8)) * (np.exp(0.0043*(i-20)))
    aproximacao_Linear2 = ((2.7)/((10)**8)) + ((2.7)/((10)**8))*0.0043*(i-20)
    if abs(Funcao3 - aproximacao_Linear2) <= 0.01*Funcao3:
        a.append(i)


print(round(min(a),1))
print(round(max(a),1))

// Saída:
// -11.4
// 54.5
```
#### Código para os gráficos

```.py
fig8, img3 = plt.subplots(figsize = (10,5))
img3.plot (t,Funcao2)
img3.plot (t,aproximacao_Linear)
img3.plot (t,1.01*Funcao2)
img3.plot (t,0.99*Funcao2)

img3.set_xlim([45,65])
img3.set_ylim([2.7*(10**(-8)),3.5*(10**(-8))])

img3.legend(['Função','aproximacao_linear','101Função','99Função'],fontsize=10)

plt.grid()
plt.show()



fig9, img4 = plt.subplots(figsize = (10,5))
img4.plot (t,Funcao2)
img4.plot (t,aproximacao_Linear)
img4.plot (t,1.01*Funcao2)
img4.plot (t,0.99*Funcao2)


limiteY = 2.4*(10**(-8))
limiteY2 = 2.3*(10**(-8))

img4.set_xlim([-13,-10])
img4.set_ylim([limiteY2,limiteY])

img4.legend(['Função','aproximacao_linear','101Função','99Função'],fontsize=10)

plt.grid()
plt.show()
```

####  Imagem focando em pontos próximos de -11.4

![](https://i.imgur.com/qr1geXF.png)


####  Imagem focando em pontos próximos de 54.5

![](https://i.imgur.com/6Oj647S.png)


## Questão 3


### a)

### b)

### c)

### d)

## Questão 4

### a)
Considerando que os polos encontrados foram -2 e -3, calculando a inversa de LaPlace pelo teorema dos resíduos, temos:

![](https://i.imgur.com/vgx9EjR.png)

### b)
Considerando o polo real -2 e os polos complexos,-2 +3i e -2 -3i, encontrados, calculando a inversa de LaPlace pelo teorema dos resíduos, temos:

![](https://i.imgur.com/cX97Qxz.png)
![](https://i.imgur.com/qTPCR4q.png)