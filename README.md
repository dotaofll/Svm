Consider a two-class classfication problem using linear models of the form

![](http://latex.codecogs.com/gif.latex?\\frac{1}{1+sin(x)})

![](http://latex.codecogs.com/gif.latex?y(\\mathbf{x})=\\omega^{T} \\boldsymbol{\\phi}(\\mathbf{x})+b(1-1))
 
$$
y(\mathbf{x})=\omega^{T} \boldsymbol{\phi}(\mathbf{x})+b(1-1)
$$

function $\boldsymbol{\phi}$ denotes a fixed feature space transformation.In the form `(1-1)` $\omega=\left(\omega_{1} ; \omega_{2} ; \ldots ; \omega_{d} ;\right)$ is the normal vector which decides the direction of the hyperplane. $b$ is the bias which defines the distance between the origin and the hyperplane.

The training dataset `D` comprises N input vectors $x=\left(x_{1} ; x_{2} ; \ldots ; x_{d} ;\right)$  with corresponding target values $r=\left(r_{1} ; r_{2} ; \ldots ; r_{m}\right)$ where $r_{n} \in\{-1,1\}$. And new data points $x$ are classified according to the sign of $y(\mathbf{x})$.

The distance from any data points $x$ to decision surface can be represented by

$$
\frac{t_{n} y\left(\mathbf{x}_{n}\right)}{\|\mathbf{w}\|}=\frac{t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right)}{\|\mathbf{w}\|}   (1-2)
$$

The margin is given by the perpendicular distance of $\mathbf{x}_{n}$ which is the closest point in the dataset to hyperplane,and we wish to optimize the parameters $\omega$ and $\mathbf{b}$ in order to maximize this distance.Thus the maximum margin solution is found by solving 

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

There are some data points in the dataset which the closest to the decision surface that make the form (1-5) equal sign true.Such points are also named the support vector.And the before mentioned Margin is the sum of the distances from positive and negative support vectors to the hyperplane,like the form (1-6):

$$
\gamma=\frac{2}{\|\omega\|} (1-6)
$$

The optimization problem then simply requires that we maximize $| | \mathbf{w}| |^{-1}$,which is equivalent to minimizing $\|\mathbf{w}\|^{2}$,and so we have to solve the optimization problem $\underset{\mathbf{w}, b}{\arg \min } \frac{1}{2}\|\mathbf{w}\|^{2}$ subject to 

$$
t_{n}\left(\mathbf{w}^{\mathrm{T}} \boldsymbol{\phi}\left(\mathbf{x}_{n}\right)+b\right) \geqslant 1, \quad n=1, \ldots, N (1-7)
$$

so until now the problem has changed.

To optimize this problem we need to understand the extremum with a constraint and a method to handle it.That`s Lagrangian multiplier.

The Lagrangian multiplier is used to solve such problem which is that is general optimization problems with equality constraints given bellow：

$$
\begin{array}{l}{\min f(\mathbf{x})} \\ {\text {s.t. } g_{j}(\mathbf{x}) \leq 0(j=1,2, \cdots, m)} \\ {h_{k}(\mathbf{x})=0(k=1,2, \cdots, l)}\end{array} (1-8)
$$

but here is an error in form (1-8).That`s this form is a inequality constraints $g_{j}(\mathbf{x}) \leq 0(j=1,2, \cdots, m)$.So if we transform such inequality problem to equality problem, the Lagrangian multiplier will make it.

Let`s give a simple example:

$$
\begin{array}{c}{\min f(x)} \\ {\text { s. } t . g_{1}(x)=a-x \leq 0} \\ {g_{2}(x)=x-b \leq 0}\end{array}
$$

For each constraint $g_{1}$ and $g_{2}$ add a relaxation variable $a_{1}^{2}$,$b_{1}^{2}$.
so form(1-8)`s constraints will be transformed to:

$$
\begin{array}{l}{h_{1}\left(x, a_{1}\right)=g_{1}(x)+a_{1}^{2}=a-x+a_{1}^{2}=0} \\ {h_{2}\left(x, b_{1}\right)=g_{2}(x)+b_{1}^{2}=x-b+b_{1}^{2}=0}\end{array}
$$

The inequality constraint is transformed to equality constraint.So we can use the Lagrangian multiplier to solve this.
Here is the equivalent constraint optimization problem:

$$
\begin{array}{l}{\min f\left(x_{1}, x_{2}, \ldots, x_{n}\right)} \\ {\text {s.t.h}_{k}\left(x_{1}, x_{2}, \ldots, x_{n}\right)=0}\end{array}
$$


Define the equation below:

$$
L(x,\lambda) = f(x) + \sum_{j=1}^{m} \lambda_{j} h_{k}(\mathbf{x})
$$

function $L(x,\lambda)$ is called the Lagrangian multiplier and the parameter $\lambda$ is called the multiplier.Calculating a partial derivative to the equation:

$$
\left\{\begin{array}{l}{\frac{\partial L}{\partial x_{i}}=0(i=1,2, \cdots, n)} \\ {\frac{\partial L}{\partial \lambda_{k}}=0(j=1,2, \cdots, m)}\end{array}\right.
$$

The obtained solution is a possibly extreme point. Since we have used the necessary conditions, whether it is an extreme point or not needs to be tested according to the specific conditions of the problem itself. This equation group is called the extreme value requirement of the equality constraint.

Let`s come back to the example that mentioned above.When we convert a inequality constraint to a equality constraint,we can use Lagrangian function the solve this.

$$
L\left(x, a_{1}, b_{1}, \mu_{1}, \mu_{2}\right)=f(x)+\mu_{1}\left(a-x+a_{1}^{2}\right)+\mu_{2}\left(x-b+b_{1}^{2}\right)
$$

We then solve the problem by the equality constraint optimization problem (extreme value necessary condition), simultaneous equation:

$$
\left\{\begin{array}{l}{\frac{\partial F}{\partial x}=\frac{\partial f}{\partial x}+\mu_{1} \frac{d g_{1}}{d x}+\mu_{2} \frac{d g_{2}}{d x}=\frac{d f}{d x}-\mu_{1}+\mu_{2}=0} \\ {\frac{\partial F}{\partial \mu_{1}}=g_{1}+a_{1}^{2}=0, \quad \frac{\partial F}{\partial \mu_{2}}=g_{2}+b_{1}^{2}=0} \\ {\frac{\partial F}{\partial a_{1}}=2 \mu_{1} a_{1}=0, \quad \frac{\partial F}{\partial b_{1}}=2 \mu_{2} b_{1}=0} \\ {\mu_{1} \geq 0, \quad \mu_{2} \geq 0}\end{array}\right.
$$

Thus, the equations (extremely necessary) are converted into:

$$
\left\{\begin{array}{l}{\frac{d f}{d x}+\mu_{1} \frac{d g_{1}}{d x}+\mu_{2} \frac{d g_{2}}{d x}=0} \\ {\mu_{1} g_{1}(x)=0, \mu_{2} g_{2}(x)=0} \\ {\mu_{1} \geq 0, \mu_{2} \geq 0}\end{array}\right.
$$

This is a one-time situation. Similarly, for multiple inequality constraints

$$
\begin{array}{l}{\min f(\mathbf{x})} \\ {\text {s.t.} g_{j}(\mathbf{x}) \leq 0(j=1,2, \cdots, m)}\end{array}
$$

and we have

$$
\left\{\begin{array}{l}{\frac{\partial f\left(x^{*}\right)}{\partial x_{i}}+\sum_{j=1}^{m} \mu_{j} \frac{\partial g_{j}\left(x^{*}\right)}{\partial x_{i}}=0(i=1,2, \ldots, n)} \\ {\mu_{j} g_{j}\left(x^{*}\right)=0(j=1,2, \ldots, m)} \\ {\mu_{j} \geq 0(j=1,2, \ldots, m)}\end{array}\right.
$$

That is so called KKT condition.

Let`s come back to our goal.Using svm to divide a dataset we must optimize this:

$$
arg \min _{\omega, b} \frac{1}{2}\|\omega\|^{2}, s . t . y\left(\omega^{T} \boldsymbol{\phi}(\mathbf{x})+b\right) \geq 1
$$

When we use the Lagrangian multiplier to solve the form that given above,we can get this:

$$
L(\omega, b, \alpha)=\frac{1}{2}\|\omega\|^{2}+\sum_{i=1}^{m} \alpha_{i}\left(1-y\left(\omega^{T} \boldsymbol{\phi}(\mathbf{x})+b\right)\right)
$$

in this form $\alpha_{i} \geq 0$ and KKT condition guarantees it.

Until now we know what the svm is and how it works.But we do not know how to compute it because there are too many parameters.
Next section I will show you how to convert this form to a dual problem which can be computed and understanded.
