> **1. Quel théorème du cours nous autorise-t-il à estimer l’espérance conditionnelle par la moyenne empirique de simulations conditionnelles.**

Rappelons le théorême de la limite centrale : 

Si les $Z_n$ sont des variables aléatoires réelles, indépendantes et de même loi, de carré intégrable, d'espérance $m$ et de variance $\sigma^2 >0$, alors les variables $\frac{S_n -nm}{\sigma \sqrt{n}}$ convergent en loi vers une variable aléatoire de loi $\N(0,1)$.

En d'autres termes, $\sqrt{n}(M_n - m)$ converge vers une variable normale de loi $\N(0,\sigma^2)$

On en déduit que $n^\alpha (\frac{S_n}{n} - m)$ converge vers 0 (resp. $+\infty$) en probabilité lorsque $\alpha < 1/2$ (resp. $\alpha > 1/2$)

En particulier pour $\alpha = 0$ : 
$$\frac{S_n}{n} \to^\mathbb{P} m$$

Soit $(\Omega,\mathcal{A},\mathbb{P}_Z)$ l'espace probabilisé. Posons $Z_n$ le resultat du  n-ème tirage avec remise d'un élément de cet espace. Les $(Z_n)_\mathbb{N}$ vérifient les ocnditions d'application du **théorême de la limite centrale**. 



D'où en considérant le vecteur aléatoire conditionnel $Y|X=x$. En notant Y les valeurs prises aux points de discretisation sans observation et X les valeurs prises par les composantes aux sites d'observation. On a alors sans perte de généralité $Z = (X,Y)$ par permutations.

La moyenne des simulations conditionelles converge vers l'espérance conditionelle. **Il est donc approprié de l'approcher de cette façon.**

> **2. Rappeler la loi conditionnelle du vecteur des composantes de Z correspondant aux points de discrétisation sans observation, connaissant les valeurs prises par les composantes aux sites d’observation.**

Le vecteur aléatoire des composantes de Z correspondant aux points de discrétisation sans observation, connaissant les valeurs prises par les composantes aux sites d’observation, est une variable aléatoire à densité et admet pour densité

En notant Y les valeurs prises aux points de discretisation sans observation et X les valeurs prises par les composantes aux sites d'observation. On a alors sans perte de généralité $Z = (X,Y)$ par permutations.

$Y|X=x$ admet une densité $f_{Y|X=x}$
telle que 
$$f_{Y|X=x} =\frac{1}{(2\pi)^{k/2}\sqrt{det(CS_Y)}}exp(-\frac{1}{2}(y-\Psi(x))^\perp CS_Y^{-1}(y-\Psi (x)))$$

où on a  :

$$
E(Y|X=x) = \Psi(z)= m_Y + C_{Y,Z}C_Z^{-1}(z-m_Z)
$$


> **3. Si Y = (Y1, . . . , Yp) est un vecteur de composantes gaussiennes indépendantes, toutes d’espérance nulle et de variance 1, quelle est la loi du vecteur Z = m + RY où R est une matrice p × p et m est un vecteur de taille p ?**

Si Y est un vecteur de composantes gaussiennes indépendantes, toutes d'esperance nulle et de variance 1,  alors on peut caractériser cette variable aléatoire par sa fonction caractéristiques $\Phi_Y(u) =e^{i<u|m>-\frac{1}{2} <u|I_n u>}$

Or d'après le cours de Probabilté $\Phi_Z(u) = \Phi_{m+RY}(u) = e^{i<u|m>}\Phi_Y(R^\perp u)$

Ce qui dans notre cas nous donne : 

$$\Phi_Z(u) = \Phi_{m+RY}(u) = e^{i<u|m>}\Phi_Y(R^\perp u)$$

Donc Z suit la loi qui a pour fonction caractéristique : 
$$
\Phi_Z(u) = \Phi_{m+RY}(u) = e^{i<u|m>-\frac{1}{2} <R^\perp u|I_n R^\perp u>}
$$


> **4. En déduire un algorithme de simulation conditionnelle.**

On en déduit donc qu'en utilisant une matrice R bien choisie on peut arriver simuler un vecteur gaussien conditionnel

En effet si on choisit la transformée de Cholesky de la matrice de covariance conditionelle C', que l'on notera R:
En posant Z'  = m +RY où Y = (Y1, . . . , Yp) est un vecteur de composantes gaussiennes indépendantes, toutes d’espérance nulle et de variance 1

$\Phi_Z'(u) = e^{i<u|m> -\frac{1}{2}<R^\perp u|R^\perp u> }
 =  e^{i< u|m> -\frac{1}{2} <u|Cu>}$ ( par symétrie de R ) 
 
$ \Phi_Z'(u) = e^{i<u| m>-\frac{1}{2} <u|Cu>}$

Donc Z' est une variable aléatoire à densité, Z' est un un vecteur gaussien

De plus Z'est de même loi que la variable aléatoire gaussienne $Z|Z(x_1, ...,x_i) = (z_1, ..., z_i)$ par identification des fonctions caractéristiqes