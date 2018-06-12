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
 3. O coeficiente de arrasto do paraquedas <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/>
A pressão dinâmica é função da velocidade e da densidade do ar, logo varia com a altitude e temperatura.

#### Velocidade Terminal
A velocidade terminal provida por um paraquedas em uma descida estável é dada por:
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/ba3dbc5fbad06d605ba58fbd4bc77060.svg?invert_in_darkmode" align=middle width=114.83745405pt height=49.3155696pt/></p>

Onde <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/b6eaf83185a33051537f482590a09dd4.svg?invert_in_darkmode" align=middle width=15.82597005pt height=22.4657235pt/> = velocidade terminal, <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/bd049554fbc115df2fe2a43a4e203ffd.svg?invert_in_darkmode" align=middle width=20.49092595pt height=22.4657235pt/>= peso do foguete + paraquedas, <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/5436a70b50756a709d69dc3c9d30f02c.svg?invert_in_darkmode" align=middle width=15.95457765pt height=22.4657235pt/> área da superfície do velame, <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/cde8f10dbe6e8fa1c4c752365b80f053.svg?invert_in_darkmode" align=middle width=21.4806009pt height=22.8310566pt/> coeficiente de arrasto e <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/4e5727f4d784156580992da9b0c9f6bb.svg?invert_in_darkmode" align=middle width=8.49888435pt height=14.1552444pt/> densidade do ar.
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
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/6a572f829d9e815fc384c69144ed071a.svg?invert_in_darkmode" align=middle width=79.34471655pt height=14.42921205pt/></p>
Ou, para determinar o <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> a partir da força de arrasto medida:
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/80b2432e4e394acba08f07e9ebfaa707.svg?invert_in_darkmode" align=middle width=65.9701944pt height=36.82577085pt/></p>
Onde <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/>=coeficiente de arrasto, <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/6af71346f7b5c6878bafdee92fe6e3df.svg?invert_in_darkmode" align=middle width=17.4138756pt height=22.4657235pt/>= força de arrasto, <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/2ec6e630f199f589a2402fdf3e0289d5.svg?invert_in_darkmode" align=middle width=8.27056725pt height=14.1552444pt/> pressão dinâmica e <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/53d147e7f3fe6e47ee05b88b166bd3f6.svg?invert_in_darkmode" align=middle width=12.32879835pt height=22.4657235pt/>=Areá da seção transversal.


Para um corpo simples como um cone, a área da seção transversal é simples de ser calculada, sendo simplesmente <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/d3c6b268293c506b7fdb63dbba0c611b.svg?invert_in_darkmode" align=middle width=29.1211041pt height=26.7617526pt/>, onde R=raio da base do cone. Entretanto para paraquedas esse não é o caso, a área de referência para ser usada no calculo do coeficiente de arrasto de um paraquedas é área da superfície do velame. Esta escolha da área de referência apenas como a projeção, embora conveniente, é menos significativa, e torna o Cd uma medida um tanto falha da eficácia de um pára-quedas.
#### Efeito de sustentação
![enter image description here](https://lh3.googleusercontent.com/-jkYD572v9Ww/WKR2SHCizOI/AAAAAAAAAKE/brIhaRniXak-wBx2z_hf68cp-TS-7QXmQCLcB/s0/paraglid.gif "paraglid.gif")
A natureza de planeio de um pára-quedas é outra razão que usar o <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> como uma medida da eficácia de um pára-quedas pode ser enganoso (Figura 1). Quando um pára-quedas desce, ele pode ter tanto uma componente descendente de velocidade como uma componente horizontal (em outras palavras, ao invés de descer em linha reta, ele descerá em um ângulo). O ar que flui em torno do pára-quedas a uma determinada velocidade <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/a9a3a4a202d80326bda413b5562d5cd1.svg?invert_in_darkmode" align=middle width=13.24203705pt height=22.4657235pt/> gera tanto forças de sustentação como de arrasto - o arrasto <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode" align=middle width=14.06623185pt height=22.4657235pt/> atuando em oposição à sua linha de movimento, e a sustentação <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/ddcb483302ed36a59286424aa5e0be17.svg?invert_in_darkmode" align=middle width=11.18724255pt height=22.4657235pt/> agindo perpendicular a este, tendendo a reduzir a velocidade de descida , Portanto, o coeficiente de arrasto medido a partir de testes de "queda livre" pode indicar um <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> significativamente maior (do que, digamos, aquele medido em um túnel de vento), como resultado deste fenômeno de sustentação.

#### Efeito oscilatório
O fluxo de ar ao redor e sobre o velame de um pára-quedas pode produzir um padrão oscilante (em espiral), ou conicidade, no movimento descendente do pára-quedas  à medida que a separação do fluxo e as forças de sucção se alternam em direção. Portanto, um pára-quedas pode ser considerado capaz de descer quer num modo de planeio, quer num modo oscilante, ou numa combinação de ambos. O deslizamento tende a prevalecer a baixas velocidades de descida, e oscilando a taxas intermediárias. O <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> resultante pode variar significativamente, dependendo do modo de descida, conforme indicado pelos seguintes dados para um pára-quedas normal de tamanho real:

| Descent velocity | Descent mode | <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/>   |
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
O <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> de um paraquedas é dependente da sua velocidade (descendente) por uma pequena faixa, a altas velocidades o <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> diminui. Isto se deve ao aumento da porosidade do tecido devido ao aumento das cargas de tensão no velame. 
Isto também pode ser influência do numero de Reynolds, já que o fluxo de ar através dos poros do tecido é uma função deste. Também, a velocidades mais elevadas, a tensão nos tirantes aumenta, afetando a forma e, portanto, a área efectiva da cobertura.

Também a altas velocidades, a tensão dos cordames aumenta afetando o formato do velame e consequentemente sua área efetiva.

#### Comprimento dos Tirantes
O diâmetro inflado (e portando a área) e formato do velame são influenciados pelo comprimento dos tirantes <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/ddcb483302ed36a59286424aa5e0be17.svg?invert_in_darkmode" align=middle width=11.18724255pt height=22.4657235pt/> em relação ao diâmetro do velame <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode" align=middle width=14.06623185pt height=22.4657235pt/>. Conforme o comprimento dos tirantes aumenta, o <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e59566d5954aef5ef721404d38cbb37c.svg?invert_in_darkmode" align=middle width=18.59192775pt height=22.4657235pt/> também aumenta. Este efeito é mais perceptivo, não surpreendentemente, quando os tirantes são curtos, por exemplo <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/20b3c92d86c6fe98c92cf4a127089684.svg?invert_in_darkmode" align=middle width=76.3949571pt height=24.657534pt/>, mas se tornam menos significantes quando <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/022c1b698f7c82d075d18ea3defac2ee.svg?invert_in_darkmode" align=middle width=63.6095229pt height=24.657534pt/>.





## Design do paraquedas
Agora que discutimos os vários fatores que afetam o desempenho de um paraquedas vamos ir ao projeto. Escrevi um programa em Python, utilizando as bibliotecas NumPy(matemática simbólica) e Matplot (plotagem de gráficos) para gerar a visualização de nosso paraquedas e também para podermos ter as medidas exatas para o corte do tecido que será utilizado na fabricação dos gomos.
Neste projeto utilizamos um velame semi-eliptico de excentricidade <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/599fd9cc1122e5d088ee459db73c0438.svg?invert_in_darkmode" align=middle width=50.5764105pt height=21.1872144pt/>, que será fabricado em <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/d0b46deac7c0bf4f6285cbeb41067c88.svg?invert_in_darkmode" align=middle width=16.4384187pt height=21.1872144pt/> gomos.
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


#### Plota o gomo (<img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/d91f1fccf3ca1e83e854e47fc1d00c85.svg?invert_in_darkmode" align=middle width=53.35601865pt height=22.4657235pt/>)
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
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/e19168b9394ea87e7f3af85e888c1a5a.svg?invert_in_darkmode" align=middle width=187.9386729pt height=16.438356pt/></p>
Onde <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode" align=middle width=8.17352745pt height=22.8310566pt/> é o angulo  de apertura de um segmento da curva.

Para uma pequena variação do angulo <img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/7e9fe18dc67705c858c077c5ee292ab4.svg?invert_in_darkmode" align=middle width=13.69867125pt height=22.4657235pt/> o segmento da curva avança:
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/4fb373cc6ce095457af819e53f47d1a1.svg?invert_in_darkmode" align=middle width=281.18560635pt height=41.27894265pt/></p>
<img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/a064ab0ce7c67dd9e0174654da6f93e2.svg?invert_in_darkmode" align=middle width=60.91321335pt height=24.657534pt/>
<img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/345f53f340f6a422e6a450a1d22b9e36.svg?invert_in_darkmode" align=middle width=261.96266085pt height=24.7161288pt/>
<img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/cd594415e39eaa79a6ac317e813b8774.svg?invert_in_darkmode" align=middle width=244.4169486pt height=24.7161288pt/>
<p align="center"><img src="https://rawgit.com/RafaelFigueiredo/recovery-system/master/svgs/c3ce9422d65668777a767b2be5f73faf.svg?invert_in_darkmode" align=middle width=541.2620631pt height=41.27894265pt/></p>


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
