# Assginement3
## 2021021699 이유원
<br>

The responsibilty of the mixture model of gaussian distribution is<br><br>
$\gamma(z_k)\equiv p(z_k=1|x)=\frac{p(z_k=1)p(x|z_k=1)}{\sum^{k}_{j=1}p(z_j=1)p(x|z_j=1)}=\frac{\pi_kN(x|\mu_k,\Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x|\mu_j, \Sigma_j)}$ <br><br>

The log-likelihood function for estimating the three paramter 
$\{\pi_k\}_{k=1}^{K},\, \{\mu_k\}_{k=1}^{K}, \, \{\Sigma_k\}_{k=1}^{K}$ is <br><br>
$L(X;\theta)=lnp(X|\pi, \mu, \Sigma) = ln\{\prod_{n=1}^{N}p(x_n|\pi,\mu,\Sigma)\}=\sum_{n=1}^{N}ln\{\sum_{k=1}^{K}\pi_kN(x_n|mu_k,\Sigma_k)\}$
<br><br>
The parameters can be represented by responsibilty.<br>
1. Mean ($\{\mu_k\}_{k=1}^{K}$)
   >$\frac{\partial L(X;\theta)}{\partial \mu_k} = \sum_{n=1}^{N}\frac{\pi_kN(x|\mu_k,\Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x|\mu_j, \Sigma_j)}\sum_{k}^{-1}(x_n-\mu_k)=0$<br><br>
   $0=-\sum_{n=1}^{N}\frac{\pi_kN(x|\mu_k,\Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x|\mu_j, \Sigma_j)}\sum_{k}(x_n-\mu_k)$<br><br>
   $\leftrightarrow \sum_{n=1}^{N}\gamma(z_{nk})(x_n - \mu_k) = 0$<br><br>
   $\therefore \mu_k = \frac{\sum_{n=1}^{N}\gamma(z_{nk})x_n}{\sum_{n=1}^{N}\gamma(z_{nk})}$

2. Covariance ($\{\Sigma_k\}_{k=1}^{K}$)
    > $\frac{\partial L(X;\theta)}{\partial \mu_k} = \sum_{n=1}^{N}\frac{\pi_kN(x|\mu_k,\Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x|\mu_j, \Sigma_j)}\{\frac{1}{2}\sum_{k}^{-1}(x_n - \mu_k)(x_n-\mu_k)^T\sum_{k}^{-1} - \frac{1}{2}\sum_{k}^{-1}\}=0$<br><br>
    $\leftrightarrow \sum_{n=1}^{N}\gamma(z_nk)\{\sum_{k}^{-1}(x_n-\mu_k)(x_n-\mu_k)^T -1\}=0$<br><br>
    $\therefore \frac{\sum_{n=1}^{N}\gamma(z_{nk})(x_n-\mu_k)(x_n-\mu_k)^T}{\sum_{n=1}^{N}\gamma(z_{nk})}$

3. Mixing coefficeint ($\{\pi_k\}_{k=1}^{K}$)
    > $J(X;\theta,\lambda) = \sum_{n=1}^{N}ln\sum_{k=1}^{K}\pi_kN(x_n|\mu_k, \Sigma_k) + \lambda(1-\sum_{k=1}^{K}\pi_k)$<br><br>
    $\frac{\partial J(X;\theta,\lambda)}{\partial \pi_k} = \sum_{n=1}^{N}\frac{N(x_n|\mu_k, \Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x_n|\mu_j, \Sigma_j)} - \lambda = 0$ <br><br>
    $\leftrightarrow \sum_{k=1}^{K}\sum_{n=1}^{N}\frac{\pi_kN(x_n|\mu_k, \Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x_n|\mu_j, \Sigma_j)} - \lambda \sum_{k=1}^{K}\pi_k = 0$<br><br>
    $\leftrightarrow \sum_{k=1}^{K}\sum_{n=1}^{N}\gamma(z_{nk})-\lambda = 0$
    <br><br>
    $\therefore \lambda = N$
    <br><br><br><br>
    $\frac{\partial J(X;\theta,\lambda)}{\partial \pi_k} = \sum_{n=1}^{N}\frac{N(x_n|\mu_k, \Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x_n|\mu_j, \Sigma_j)} - N = 0$<br><br>
    $\leftrightarrow \frac{\partial J(X;\theta,\lambda)}{\partial \pi_k} = \sum_{n=1}^{N}\frac{N(x_n|\mu_k, \Sigma_k)}{\sum_{j=1}^{K}\pi_jN(x_n|\mu_j, \Sigma_j)} - N\pi_k = 0$
    <br><br>
    $\therefore \pi_k = \frac{1}{N}\sum_{n=1}^{N}\gamma(z_{nk})$

    

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: {inlineMath: [['$', '$']]}, messageStyle: "none" });</script>
