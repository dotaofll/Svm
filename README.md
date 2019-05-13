# Introduce SVM

Consider a two-class classfication problem using linear models of the form

$$
y(\mathbf{x})=\omega^{T} f(\mathbf{x})+b
$$



function $f$ denotes a fixed feature space transformation.In the form `(1-1)` $\omega=\left(\omega_{1} ; \omega_{2} ; \ldots ; \omega_{d} ;\right)$ is the normal vector which decides the direction of the hyperplane. $b$ is the bias which defines the distance between the origin and the hyperplane.

The training dataset `D` comprises N input vectors $x=\left(x_{1} ; x_{2} ; \ldots ; x_{d} ;\right)$  with corresponding target values $r=\left(r_{1} ; r_{2} ; \ldots ; r_{m}\right)$ where $r_{n} \in\{-1,1\}$. And new data points $x$ are classfied according to the sign of $y(\mathbf{x})$.

The distance that any data points $x$ to decision surface can represented by

$$
\frac{t_{n} y\left(\mathbf{x}_{n}\right)}{\|\mathbf{w}\|}=\frac{t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right)}{\|\mathbf{w}\|}   (1-2)
$$



The margin is given by the perpendicular distance to the cloest point $\mathbf{X}_{n}$ from the data set,and we wish to optimize the parameters $\omega$ and $\mathbf{b}$ in order to maximize this distance.Thus the maximum margin solution is found by solving 

$$
\underset{\mathbf{w}, b}{\arg \max }\left\{\frac{1}{\|\mathbf{w}\|} \min _{n}\left[t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right)\right]\right\} (1-3)
$$

We assume that the svm can correctly classify the dataset.Given data point $\left(x_{i}, y_{i}\right) \in D$ there is the following expression:

$$
\left\{\begin{array}{ll}{\omega^{T} \boldsymbol{\phi}(x_{i})+b>0,} & {y_{i}=+1} \\ {\omega^{T} \boldsymbol{\phi}(x_{i})+b<0,} & {y_{i}=-1}\end{array}\right.  (1-4)
$$

but here is a constraint:

$$
\left\{\begin{array}{ll}{\omega^{T} \boldsymbol{\phi}(x_{i})+b>+1,} & {y_{i}=+1} \\ {\omega^{T} \boldsymbol{\phi}(x_{i})+b<-1,} & {y_{i}=-1}\end{array}\right. (1-5)
$$

There are some data points in the dataset which the closest to the decision surface that make the form (1-5) equal sign.Such points are also called the support vector.And the so called Margin is the distance between the form (1-5):
$$
\gamma=\frac{2}{\|\omega\|} (1-6)
$$

The optimization problem then simply requires that we maximize $| | \mathbf{w}| |^{-1}$,which is equivalent to minimizing $\|\mathbf{w}\|^{2}$,and so we have to solve the optimization problem $\underset{\mathbf{w}, b}{\arg \min } \frac{1}{2}\|\mathbf{w}\|^{2}$ subject to 

$$
t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right) \geqslant 1, \quad n=1, \ldots, N (1-7)
$$
<a href="https://www.codecogs.com/eqnedit.php?latex=\fn_cm&space;$$&space;t_{n}\left(\mathbf{w}^{\mathrm{T}}&space;\boldsymbol{\phi}\left(\mathbf{x}_{n}\right)&plus;b\right)&space;\geqslant&space;1,&space;\quad&space;n=1,&space;\ldots,&space;N&space;(1-7)&space;$$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\fn_cm&space;$$&space;t_{n}\left(\mathbf{w}^{\mathrm{T}}&space;\boldsymbol{\phi}\left(\mathbf{x}_{n}\right)&plus;b\right)&space;\geqslant&space;1,&space;\quad&space;n=1,&space;\ldots,&space;N&space;(1-7)&space;$$" title="$$ t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right) \geqslant 1, \quad n=1, \ldots, N (1-7) $$" /></a>

so until now the problem has changed.

