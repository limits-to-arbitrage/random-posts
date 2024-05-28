## Deriving the formula for reducible vs. irreducible error on page 18
On page 18, when discussing the difference between reducible and irreducible error, the text notes that

```math
E(Y-\hat{Y})^2=\big(f(X)-\hat{f}(X)\big)^2+Var(\varepsilon)
```
where $f$ is the true data generating process, $\hat{f}$ is an estimate of the data generating process, and $X$ is the set of predictors. The text notes the above is "easy to show". Below, I walk through how to do so.

First note the left-hand side of the above can be more clearly written as

```math
E[(Y-\hat{Y})^2]
```

and, because $Y=f(X)+\varepsilon$ and $\hat{Y}=\hat{f}(X)$, we have that
```math
E[(Y-\hat{Y})^2]
=E[\big(f(X)+\varepsilon-\hat{f}(X)\big)^2]
```
```math
=E[f^2(X)+f(X)\varepsilon-f(X)\hat{f}(X)+f(X)\varepsilon+\varepsilon^2+\hat{f}(X)\varepsilon-f(X)\hat{f}(X)-\hat{f}(X)\varepsilon+\hat{f}^2(X)].
```
By the linearity of expectation, the above simplifies to
```math
=E[f^2(X)]+E[f(X)\varepsilon]-E[f(X)\hat{f}(X)]+E[f(X)\varepsilon]+E[\varepsilon^2]+E[\hat{f}(X)\varepsilon]-E[f(X)\hat{f}(X)]-E[\hat{f}(X)\varepsilon]+E[\hat{f}^2(X)]
```
and as $f$, $\hat{f}$, and $X$ are considered fixed, we have
```math
=f^2(X)+f(X)E[\varepsilon]-f(X)\hat{f}(X)+f(X)E[\varepsilon]+E[\varepsilon^2]+\hat{f}(X)E[\varepsilon]-f(X)\hat{f}(X)-\hat{f}E[(X)\varepsilon]+\hat{f}^2(X).
```
As $E[\varepsilon]=0$, we have
```math
=f^2(X)-f(X)\hat{f}(X)+E[\varepsilon^2]-f(X)\hat{f}(X)+\hat{f}^2(X).
```
Then, by grouping like terms as follows
```math
=f^2(X)-2f(X)\hat{f}(X)+\hat{f}^2(X)+E[\varepsilon^2]
```
the above can be factored as
```math
=\big(f^2(X)-\hat{f}(X)\big)^2+E[\varepsilon^2].
```
Then, as $Var(\varepsilon)=E[\varepsilon^2]-E[\varepsilon]^2$, $E[\varepsilon]=0\Rightarrow Var(\varepsilon)=E[\varepsilon^2]$, and we have that the above is equivalent to
```math
=\big(f(X)-\hat{f}(X)\big)^2+Var(\varepsilon)
```
that is,
```math
E(Y-\hat{Y})^2=\big(f(X)-\hat{f}(X)\big)^2+Var(\varepsilon)
```
as was to be shown.
