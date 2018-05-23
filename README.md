# Sistema de Recuperação

## Introdução
O sistema de recuperação deve garantir a desaceleração do foguete a uma velocidade terminal aceitável, visando assim salvaguardar pessoas e materiais nas áreas próximas do local de lançamento.  
O sistema de recuperação se divide em duas etapas essenciais:  
 1. Detectar o apogeu ou evento anormal que torne necessário disparar o paraquedas.
A detecção desses eventos é feita pela análise dos dados barométrico, agulha giroscópica e acelerômetro.  
 2. Sistema de ejeção dos paraquedas, seja por atuadores mecânicos, pneumáticos ou pirotécnicos. Pela confiabilidade histórica, para este projeto foram escolhidos atuadores pirotécnicos.  


## Plano de vôo
A eletrônica embarcada do deve ser capaz de detectar as diversas condições de voo que o foguete pode apresentar.  Antes de avaliar cada caso em que o foguete deve usar seu sistema de recuperação, vamos apresentar o *conceito de operação (Conops)*, que pode ser:
 - Normal: Liberar paraquedas precursor para desaceleração inicial e queda controlada com velocidade terminal desejada de 25m/s e posterior liberação do paraquedas principal a altitude 300~200 metros para reduzir a velocidade terminal a 5m/s até o foguete tocar o solo.  
O precursor tem seu tamanho reduzido pois assim o estresse estrutural é menor e ele pode suportar a alta velocidade do foguete, também devido a seu tamanho reduzido o foguete não será "carregado" pelo vento para uma área muito distante do ponto de lançamento.  
 - Emergência: Liberar precursor para que este puxe o paraquedas principal imediatamente.  
 ![enter image description here](https://lh3.googleusercontent.com/-pDPI2aDdhVc/WKPPegubQZI/AAAAAAAAAJg/6-T8RDsxnUcM_oD7M6RWrq8tdyikznrOACLcB/s0/image18.png "conops.png")

 - **Caso 1 (apogeu exato)** o foguete tem após sua fase propulsada um voo inercial perfeito, atingindo o apogeu de projeto perfeitamente. Neste caso o paraquedas precursor é disparado no apogeu seguindo o *conops normal*.  
 - **Caso 2 (apogeu baixo)** o foguete tem sua fase propulsada deficiente, ou as condições de vento foram desfavoráveis (ventos descendentes), mas conseguiu atingir um teto maior que o limite de segurança 200 metros. Neste caso o foguete também segue o *conops normal*.  
 -  **Caso 3 (menor que o teto limite de 200 metros )** fase propulsada deficiente ou instabilidade aerodinâmica fez com que o foguete se alinhasse com o vento e voa-se com um angulo baixo, o paraquedas principal deve ser liberado seguindo o *conops emergência*.  
 - **Caso 4 (perda de rumo)** devido ao vento forte ou destruição de uma das alhetas na saída do trilho de lançamento o foguete é incapaz de permanecer na vertical. Se a altitude for acima da minima de 200 metros seguir conceito operacional *normal*, senão o conceito *emergência*.  


## Detecção de Apogeu
## Paraquedas
#### Aerodinâmica
A velocidade de queda de qualquer objeto (como um foguete) equipado com paraquedas é dependente da força de arrasto que o paraquedas desenvolve para anular a força gravitacional devido a massa da carga.
A força de arrasto é dependente da:
 1. Pressão dinâmica criada pelo ar em movimento pressionando o velame do paraquedas (é o que mantém o paraquedas inflado).
 2. O diâmetro do paraquedas, que determina a área em que a pressão dinâmica atua.
 3. O coeficiente de arrasto do paraquedas $C_d$
A pressão dinâmica é função da velocidade e da densidade do ar, logo varia com a altitude e temperatura.

#### Velocidade Terminal
A velocidade terminal provida por um paraquedas em uma descida estável é dada por:
$$ V_e=\sqrt{\frac{2W_t}{S_c.Cd.\rho}} $$

Onde $ V_e $ = velocidade terminal, $W_t$= peso do foguete + paraquedas, $ S_c $ área da superfície do velame, $Cd $ coeficiente de arrasto e $ \rho $ densidade do ar.
#### Coeficiente de Arrasto
O coeficiente de arrasto de qualquer paraquedas é dependente de vários fatores, entre eles:
 - Características de planar( gerar sustentação)
 - Padrão do fluxo de ar ao redor do paraquedas
 - Formato do velame
 - Permeabilidade do tecido ("aperto" da trama)
 - Velocidade de queda
 - Comprimento dos cabos.
O coeficiente de arrasto é usualmente obtido por testes, seja em um túnel de vento ou por teste de queda, e é determinado pela medida da força de arrasto a determinada velocidade (pressão dinâmica)
A equação empregada é:
$$F_d=p A C_d$$
Ou, para determinar o $C_d$ a partir da força de arrasto medida:
$$Cd=\frac{F_d}{p A}$$
Onde $C_d$=coeficiente de arrasto, $F_d$= força de arrasto, $p$ pressão dinâmica e $A$=Areá da seção transversal.


Para um corpo simples como um cone, a área da seção transversal é simples de ser calculada, sendo simplesmente $\pi R^2$, onde R=raio da base do cone. Entretanto para paraquedas esse não é o caso, a área de referência para ser usada no calculo do coeficiente de arrasto de um paraquedas é área da superfície do velame. Esta escolha da área de referência apenas como a projeção, embora conveniente, é menos significativa, e torna o Cd uma medida um tanto falha da eficácia de um pára-quedas.
#### Efeito de sustentação
![enter image description here](https://lh3.googleusercontent.com/-jkYD572v9Ww/WKR2SHCizOI/AAAAAAAAAKE/brIhaRniXak-wBx2z_hf68cp-TS-7QXmQCLcB/s0/paraglid.gif "paraglid.gif")
A natureza de planeio de um pára-quedas é outra razão que usar o $C_d$ como uma medida da eficácia de um pára-quedas pode ser enganoso (Figura 1). Quando um pára-quedas desce, ele pode ter tanto uma componente descendente de velocidade como uma componente horizontal (em outras palavras, ao invés de descer em linha reta, ele descerá em um ângulo). O ar que flui em torno do pára-quedas a uma determinada velocidade $V$ gera tanto forças de sustentação como de arrasto - o arrasto $D$ atuando em oposição à sua linha de movimento, e a sustentação $L$ agindo perpendicular a este, tendendo a reduzir a velocidade de descida , Portanto, o coeficiente de arrasto medido a partir de testes de "queda livre" pode indicar um $C_d$ significativamente maior (do que, digamos, aquele medido em um túnel de vento), como resultado deste fenômeno de sustentação.

#### Efeito oscilatório
O fluxo de ar ao redor e sobre o velame de um pára-quedas pode produzir um padrão oscilante (em espiral), ou conicidade, no movimento descendente do pára-quedas  à medida que a separação do fluxo e as forças de sucção se alternam em direção. Portanto, um pára-quedas pode ser considerado capaz de descer quer num modo de planeio, quer num modo oscilante, ou numa combinação de ambos. O deslizamento tende a prevalecer a baixas velocidades de descida, e oscilando a taxas intermediárias. O $C_d$ resultante pode variar significativamente, dependendo do modo de descida, conforme indicado pelos seguintes dados para um pára-quedas normal de tamanho real:

| Descent velocity | Descent mode | $C_d$   |
|---|---|---|
|23 fps	|restrained	|1.26|
|20 fps	|oscillating	|1.60|
|16 fps	|gliding	|2.40|


### Fatores que influenciam o coeficiente de arrasto

#### Formado do velame
O formato do velame, seja hemisférico, semi-elíptico ou parasheet, não tem efeito significante no coeficiente de arrasto. Em vez disso a diferença na forma está relacionada a "eficiência aerodinâmica", ou seja, o coeficiente de arrasto pela área da superfície do velame. Um velame tipo semi-elíptico emprega significantemente menos tecido que um hemisférico e esta é uma consideração importante para foguetes, onde massa e volume devem ser minimizados.
#### Influência da permeabilidade do tecido
A permeabilidade, que quantifica a velocidade do ar através do material do velame é dependente da porosidade do tecido deste. A porosidade é influenciada basicamente pelo aperto da trama. O coeficiente de arrasto não é drasticamente influenciado pela permeabilidade, desde que a porosidade não seja excessiva. Seguindo essa perspectiva, qualquer tecido com um razoável aperto na trama pode ser utilizado.

#### Altas velocidades
O $C_d$ de um paraquedas é dependente da sua velocidade (descendente) por uma pequena faixa, a altas velocidades o $C_d$ diminui. Isto se deve ao aumento da porosidade do tecido devido ao aumento das cargas de tensão no velame. 
Isto também pode ser influência do numero de Reynolds, já que o fluxo de ar através dos poros do tecido é uma função deste. Também, a velocidades mais elevadas, a tensão nos tirantes aumenta, afetando a forma e, portanto, a área efectiva da cobertura.

Também a altas velocidades, a tensão dos cordames aumenta afetando o formato do velame e consequentemente sua área efetiva.

#### Comprimento dos Tirantes
O diâmetro inflado (e portando a área) e formato do velame são influenciados pelo comprimento dos tirantes $L$ em relação ao diâmetro do velame $D$. Conforme o comprimento dos tirantes aumenta, o $C_d$ também aumenta. Este efeito é mais perceptivo, não surpreendentemente, quando os tirantes são curtos, por exemplo $L/D <0.5$, mas se tornam menos significantes quando $L/D>1$.





## Design do paraquedas
Agora que discutimos os vários fatores que afetam o desempenho de um paraquedas vamos ir ao projeto. Escrevi um programa em Python, utilizando as bibliotecas NumPy(matemática simbólica) e Matplot (plotagem de gráficos) para gerar a visualização de nosso paraquedas e também para podermos ter as medidas exatas para o corte do tecido que será utilizado na fabricação dos gomos.
Neste projeto utilizamos um velame semi-eliptico de excentricidade $e=0.7$, que será fabricado em $12$ gomos.
#### Plota o velame
![enter image description here](https://lh3.googleusercontent.com/-frmqum3YjkY/WKZ3GpD_j7I/AAAAAAAAAL0/Dg97CChvnOgNNrIbqYGlhvn5s7QhGozzACLcB/s0/velame.png "velame.png")

    import numpy as np
    import matplotlib.pyplot as plt
    import mpl_toolkits.mplot3d.axes3d as axes3d
    
    
    #parametros do paraquedas
    D=100   #diametro (cm)
    e=0.7   #excentricidade da elipse a/b
    N=12    #nº de gomos
    
    #dados da geometria
    a=D/2
    b=a*e
    
    #parametrização esférica
    theta, phi = np.linspace(0, 2 * np.pi, 30), np.linspace(0, np.pi/2, 30)
    THETA, PHI = np.meshgrid(theta, phi)
    
    X = a * np.sin(PHI) * np.cos(THETA)
    Y = a * np.sin(PHI) * np.sin(THETA)
    Z = b * np.cos(PHI)
    
    #plota a imagem
    fig = plt.figure()
    ax = fig.add_subplot(1,1,1, projection='3d')
    #ax.plot_surface(x, y, z, cmap=plt.cm.YlGnBu_r)
    plot = ax.plot_surface(
        X, Y, Z, rstride=1, cstride=1, cmap=plt.cm.YlGnBu_r,
        linewidth=0, antialiased=False, alpha=0.5)
    
    ax.set_xlim(-50, 50) 
    ax.set_ylim(-50, 50) 
    ax.set_zlim(-50, 50) 
    plt.show()


#### Plota o gomo ($N=12$)
![enter image description here](https://lh3.googleusercontent.com/-eRCUuPSnLyY/WKZ4futCA9I/AAAAAAAAAMA/Va6KnnxlhbELmgO67zIzCXNAsIzGlah2QCLcB/s0/gomo.png "gomo.png")

    #plota o gomo
    gtheta = np.linspace(0-np.pi/2, -np.pi/2+(2 * np.pi / N), 30)
    GTHETA, PHI = np.meshgrid(gtheta, phi)
    
    X = a * np.sin(PHI) * 
    
    np.cos(GTHETA)
        Y = a * np.sin(PHI) * np.sin(GTHETA)
        Z = b * np.cos(PHI)
        
        
        fig = plt.figure()
        ax = fig.add_subplot(1,1,1, projection='3d')
        
        plot = ax.plot_surface(
            X, Y, Z, rstride=1, cstride=1, cmap=plt.get_cmap('plasma'),
            linewidth=0, antialiased=False, alpha=0.5)
        
        ax.set_xlim(-50, 50) 
        ax.set_ylim(-50, 50) 
        ax.set_zlim(-50, 50) 
        plt.show()

#### Planificação do gomo para corte do tecido
Se pegarmos o plano interceptando transversalmente a superfície do gomo este projetará sobre ele a parte de uma elipse no primeiro quadrante. Esta curva pode ser parametrizada como:
$$x=a.cost(\theta ); y=b.sin(\theta) $$
Onde $\theta$ é o angulo  de apertura de um segmento da curva.

Para uma pequena variação do angulo $\Delta$ o segmento da curva avança:
$$\int_{\theta}^{\theta+\Delta\theta} f(x(\theta),y(\theta))\sqrt{{x}'(\theta)^2 + {y}'(\theta)^2 } d\theta$$
$f(\theta)=1$
$x(\theta)=a.cos(\theta) \rightarrow x'(\theta)=-a.sin(\theta)$
$y(\theta)=b.sin(\theta) \rightarrow y'(\theta)=b.cos(\theta) \\$
$$\int_{\theta}^{\theta+\Delta\theta} \sqrt{[-a.sin(\theta)]^2 + [b.cos(\theta)]^2 } d\theta \rightarrow
\int_{\theta}^{\theta+\Delta\theta} \sqrt{a^2.sin^2(\theta) + b^2.cos^2(\theta) } d\theta  $$


Intregral de linha

## Sistema de ejeção do paraquedas
Nosso sistema é uma adaptação do sistema mostrado abaixo.

![http://www.nakka-rocketry.net/pix/parachutesystem.gif](https://lh3.googleusercontent.com/-1MT5a-8NAeo/WKWtdZfNe8I/AAAAAAAAAKw/4ydAuoccD1okiZ1YjdrfJxihfLGEwnykACLcB/s0/parachutesystem.gif "parachutesystem.gif")

O sistema embarcado envia um sinal de 9 volts que aquece uma resistência de alumel (95%Al+5%Ni) dispara um pequena carga pirotécnica (pólvora ou KNSU). A expansão dos gases dentro da coifa empurra o pistão feito em impressora 3D (filamento ABS, densidade máxima), separando a coifa do restante do foguete e liberando o paraquedas precursor.  
O paraquedas principal permanece preso a estrutura por uma trava ligada a um servo motor, quando o sistema embarcado detecta a altitude correta ou em um dos casos de emergência discutidos anteriormente, essa trava vai para posição "aberta" e o paraquedas precursor puxar o paraquedas principal de dentro do corpo do foguete, possibilitando assim sua abertura.

## Referências
1. http://www.nakka-rocketry.net/paracon.html
2. Parachute Recovery Systems. Design Manual by. Theo W. Knacke. Contractor for the. Recovery Systems Division. Aerosysteme Department. MARCH 1991. (http://www.dtic.mil/dtic/tr/fulltext/u2/a247666.pd
3. https://www.continuum.io/anaconda-overview
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMjA0ODI1MzBdfQ==
-->
