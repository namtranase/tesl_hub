# Linear Models and Least Squares
Classic problem: Given $X^T = (X_1 , X_2 , . . . , X_p )$ , predict: $Ŷ = β̂_0 + \sum_{j=1}^{p} X_{j} β̂_j$. For convinience, treat $β̂_0$ is one of the vector $β̂$, we have: $Ŷ = X^{T}β̂$ 

- The most popular is the _least squares_: We pick the coef $\beta$ to minimize the residual sum of squares!
![chapter2_1.png](./pictures/chapter2_1.png)
- It can be view as the matrix form:
![chapter2_2.png](./pictures/chapter2_2.png)
Where $X[N*p]$  and $y[N]$.  Differentiating with respect to $β$ we get the normal equations:

$X^T(y − Xβ) = 0$

- If $X^T X$ is a [Nonsingular matrix](https://mathworld.wolfram.com/NonsingularMatrix.html#:~:text=A%20square%20matrix%20that%20is,45), the unique solution:

$β̂ = (X^T X)^{−1} X^T y$

=> At an arbitrary input $x_0$ the prediction is $ŷ(x_0) = x^{T}_{0} β̂$ 

# Statistical Decision Theory
_The world of random variables and probability spaces_
Let define the probem: We have $X ∈ R^p$ (random variable),  $Y ∈ R$ is a real value output. With joint distribution $Pr(X, Y)$. The output function $f(X) = Y$ and the loss function is: $L(Y, f(x))$
Usually we choose the square error loss: $L(Y, f (X)) = (Y − f (X))^2$. 

The expected (squared) prediction error:
![chapter2_3.png](./pictures/chapter2_3.png)       ($E(x) = \int{xdx}$)

By apply the product rule: $Pr(X, Y ) = Pr(Y |X)Pr(X)$ for above equation, we have:
![chapter2_4.png](./pictures/chapter2_4.png)

To minimize the $EPE$, we have suffice condition:
$f (x) = argmin_c E_{Y|X} [Y − c]^2 |X = x)$, because $E_X$ is based on input data.
=> $f(x) = E(Y|X=x)$
=> The best prediction of $Y$ at any point $X = x$ is the conditional mean.

_One thing important is everthing can be express by probability theory_

Exemple with k-nearest neighbors and linear regression:
- k-nearest neighbors approximate the $f(x) = Ave(y_i |x_i ∈ N_k (x))$. Where “Ave” denotes average, and $N_k (x)$ is the neighborhood containing the $k$ points in $T$ closest to $x$. For large training, $k/N → 0$ then:
     $f (x) → E(Y |X = x)$ 
- linear regression, we have $f(x) ≈ x^T β$ and differentiating we can solve for β theoretically:
    $β = [E(XX^T)]^{−1} E(XY )$

=> So both k-nearest neighbors and least squares end up approximating conditional expectations by averages. Butm there are different:
- Least squares assumes $f(x)$ is well approximated by a globally linear function.
- k-nearest neighbors assumes $f (x)$ is well approximated by a locally constant function.






# Local Methods in High Dimensions
