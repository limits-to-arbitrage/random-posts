## Simple derivation of bias-variance trade-off for MSE on page 32
The book provides the following equation relating the expected test MSE to bias and variance as
```math
E\big(y_0-\hat{f}(x_0)\big)^2=Var\big(\hat{f}(x_0)\big)+\big[Bias(\hat{f}(x_0))\big]^2+Var(\varepsilon)
```
but does not provide a derviation. A simple derivation follows.

First, rewrite the left-hand side of the given equation as
```math
E\big[\big(y_0-\hat{f}(x_0)\big)^2\big].
```
Then, expand the above as
```math
E\big[\big(y_0-\hat{f}(x_0)\big)^2\big]=E\big[y^2_0-2y_0\hat{f}(x_0)+\hat{f}^2(x_0)\big].
```
By the linearity of expectation, the above is equal to
```math
=E[y^2_0]-2E[y_0\hat{f}(x_0)]+E[\hat{f}^2(x_0)].
```
As $y_0=f(x_0)+\varepsilon$, we have that $E[y^2_0]=E[(f(x_0)+\varepsilon)^2]=E[f^2(x_0)+2f(x_0)\varepsilon+\varepsilon^2]=E[f^2(x_0)]+2E[f(x_0)\varepsilon]+E[\varepsilon^2]$, where $E[f(x_0)\varepsilon]=E[f(x_0)]E[\varepsilon]$ by indepedence and $E[\varepsilon^2]=Var(\varepsilon)$ as $E[\varepsilon]=0\Rightarrow Var(\varepsilon)=E[\varepsilon^2]-E[\varepsilon]^2=E[\varepsilon^2]$, so that $E[f^2(x_0)]+2E[f(x_0)\varepsilon]+E[\varepsilon^2]=E[f^2(x_0)]+2E[f(x_0)]E[\varepsilon]+Var(\varepsilon)=f^2(x_0)+Var(\varepsilon)$, where $E[f^2(x_0)]=f^2(x_0)$ because $f$ is "fixed". Then by substitution, the above can be written as
```math
=f^2(x_0)+Var(\varepsilon)-2E[y_0\hat{f}(x_0)]+E[\hat{f}^2(x_0)].
```
Similarly, as $y_0=f(x_0)+\varepsilon$, we have that $E[y_0\hat{f}(x_0)]=E[(f(x_0)+\varepsilon)\hat{f}(x_0)]=E[f(x_0)\hat{f}(x_0)+\varepsilon\hat{f}(x_0)]=E[f(x_0)\hat{f}(x_0)]+E[\varepsilon\hat{f}(x_0)]$, where $E[f(x_0)\hat{f}(x_0)]=f(x_0)E[\hat{f}(x_0)]$ because $f$ is "fixed", and where $E[\varepsilon\hat{f}(x_0)]=E[\varepsilon]E[\hat{f}(x_0)]$ by independence. Then as $E[\varepsilon]=0$, we have that $E[f(x_0)\hat{f}(x_0)]+E[\varepsilon\hat{f}(x_0)]=f(x_0)E[\hat{f}(x_0)]+E[\varepsilon]E[\hat{f}(x_0)]=f(x_0)E[\hat{f}(x_0)]$. Then by substitution, the above can be written as
```math
=f^2(x_0)+Var(\varepsilon)-2f(x_0)E[\hat{f}(x_0)]+E[\hat{f}^2(x_0)].
```
Then, as $Var(\hat{f}(x_0))=E[\hat{f}^2(x_0)]-E[\hat{f}(x_0)]^2\Rightarrow E[\hat{f}^2(x_0)]=Var(\hat{f}(x_0))+E[\hat{f}(x_0)]^2$, the above can be written as
```math
=f^2(x_0)+Var(\varepsilon)-2f(x_0)E[\hat{f}(x_0)]+Var(\hat{f}(x_0))+E[\hat{f}(x_0)]^2.
```
By grouping terms as follows
```math
=Var(\hat{f}(x_0))+f^2(x_0)-2f(x_0)E[\hat{f}(x_0)]+E[\hat{f}(x_0)]^2+Var(\varepsilon)
```
the above can be factored as
```math
=Var(\hat{f}(x_0))+\big(f(x_0)-E[\hat{f}(x_0)]\big)^2+Var(\varepsilon)
```
that is, we have that
```math
E\big(y_0-\hat{f}(x_0)\big)^2=Var(\hat{f}(x_0))+\big(f(x_0)-E[\hat{f}(x_0)]\big)^2+Var(\varepsilon).
```
Finally, note that $Bias\big(\hat{f}(x_0)\big)=f(x_0)-E[\hat{f}(x_0)]$, so that, by substitution, we have that
```math
E\big(y_0-\hat{f}(x_0)\big)^2=Var(\hat{f}(x_0))+\big[Bias\big(\hat{f}(x_0)\big)\big]^2+Var(\varepsilon)
```
as was to be shown.
