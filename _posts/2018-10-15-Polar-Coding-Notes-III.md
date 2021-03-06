---
title:   Polar Coding Notes III
description: 
categories: Digital Comunication
---

>  For any B-DMC $$W$$, the channels $$\{W_N^{(i)}\}$$ polarize in the sense that, for any fixed $$\delta \in (0, 1)$$, as $$N$$ goes to infinity through powers of two, the fraction of indices $$i \in \{1, \dots, N\}$$ for which $$I(W_N^{(i)}) \in (1 − \delta, 1]$$ goes to $$I(W)$$ and the fraction for which $$I(W_N^{(i)}) \in [0, \delta)$$ goes to $$1−I(W)^{[1]}$$.
  
#### **Mrs. Gerber’s Lemma**  
Mrs. Gerber’s Lemma provides a lower bound on the entropy of the modulo-$$2$$ sum of two binary random vectors$$^{[2][3]}$$.  
Let $$h^{-1} : [0, 1] \to [0, 1/2]$$ be the inverse of the binary entropy function $$h(p) = -p\log p - (1-p)\log(1-p)$$.  
Here we set a binary symmetric channal with crossover probability $$p_0$$.  
The *convolution* of $$a$$ and $$b$$ is denoted by  
<center>$$a \ast b := a(1 − b) + (1 − a)b$$</center>  
**Convex**: The function $$f(u) = h(h^{-1}(u)\ast p_0), u \in [0,1]$$ is convex in $$u$$ for every fixed $$p_0 \in (0,1/2]^{[2]}$$.  
**Scalar MGL**: Let $$X$$ be a binary random variable and let $$U$$ be an arbitrary random variable. If $$Z \sim Bern(p)$$ is independent of $$(X, U)$$ and $$Y = X \oplus Z$$, then
<center>$$h(Y|U) \ge h\big(h^{−1}(h(X|U)) \ast p\big)$$</center> 
**Vector MGL**: Let $$X^n$$ be a binary random vector and $$U$$ be an arbitrary random variable. If $$Z^n$$ is a vector of independent and identically distributed $$Bern(p)$$ random variables independent of $$(X^n, U)$$ and $$Y^n = X^n \oplus Z^n$$, then  
<center>$${h(Y^n|U) \over n} \ge h\big(h^{−1}({h(X^n|U) \over n}) \ast p\big)$$</center>  
Let $$X,Y$$ are two binary random variable, from$$^{[2]}$$  
<center>$$H(X|Y) = \sum_{y\in\{0,1\}} p(Y=y)H(X|Y=y) \tag{conditional entropy definition}$$</center>  
Let  
<center>$$\beta_0(y) = p(X=1|Y=y) \tag{1}$$</center>  
<center>$$1 - \beta_0(y) = p(X=0|Y=y)$$</center>  
Then    
<center>$$\begin{align} H(X|Y=y) &= \sum_{x\in\{0,1\}} p(x|y)\log p(x|y) \tag{conditional entropy definition} \\&= h(\beta_0(y)) \tag{2}\end{align}$$</center>  
So that  
<center>$$h^{-1}(H(X|Y=y)) = p(X=1|Y=y) \tag{3}$$</center>  
and  
<center>$$\begin{align} H(X|Y) &= \sum_{y\in\{0,1\}} p(Y=y)H(X|Y=y) \\&= \sum_{y\in\{0,1\}} p(Y=y)h(\beta_0(y)) \\&= Eh(\beta_0) \tag{$\beta_0(y)=p(X=1|Y)$ as a RV} \end{align}$$</center>  
Let us consider first  
<center>$$\begin{align} H(X_1,X_2, ... ,X_n) &= \sum_{i=1}^n H(X_i|X_{i-1}, ... , X_1) \\&= \sum_{i=1}^n Eh(\beta_k) \tag{$\beta_k = p(X_k=1 | X_1, ... , X_{k-1}), 1 \le k \le n$} \end{align}$$</center>  
Now we have  
<center>$$\begin{align} p(Y_k=1 | X_1, ... , X_{k-1}) &= \sum_{X_k \in \{0,1\}} p(Y_k | X_k) p(X_k | X_1, ... , X_{k-1}) \\&= p_0 \ast \beta_k \end{align}$$</center>  
and  
<center>$$H(Y_k=1 | X_1, ... , X_{k-1}) = Eh(p_0 \ast \beta_k)$$</center>  
#### **Strict Polarization for Binary-Input Channels**  
First notice that  
<center>$$\begin{align} I(W^-) &= I(U_1; Y_1,Y_2) \\&=  I(X_1+X_2; Y_1,Y_2) \\&= H(X_1+X_2) - H(X_1+X_2|Y_1,Y_2) \end{align}$$</center>  
and  
<center>$$I(W) = I(X_1; Y_1) = 1- H(X_1|Y_1)$$</center>  
Since $$H(X_1|Y_1) \in (0, 1)$$, there exists an $$\alpha \in (0, 1/2)$$ such that $$H(X_1|Y_1) = h(\alpha)$$.  
<center>$$\begin{align} H(X_1+X_2|Y_1,Y_2) &= \sum_{y_1,y_2} p(y_1)p(y_2)H(X_1+X_2|y_1y_2) \\&= \sum_{y_1,y_2} p(y_1)p(y_2)h\big(\beta_0(y_1,y_2)\big) \tag{from (2)} \\&= \sum_{y_1,y_2} p(y_1)p(y_2)h\big(p(X_1+X_2 = 1|y_1y_2)\big) \tag{from (1)} \\&= \sum_{y_1,y_2} p(y_1)p(y_2)h\big(p(X_1=1|y_1)p(X_2=0|y_2) + p(X_1=0|y_1)p(X_2=1|y_2)\big) \\&= \sum_{y_1,y_2} p(y_1)p(y_2)h\big(p(X_1=1|y_1)\ast p(X_2=1|y_2)\big) \\&= \sum_{y_1,y_2} p(y_1)p(y_2)h\Big(h^{-1}\big(H(X_1|y_1)\big)\ast h^{-1}\big(H(X_2|y_2)\big)\Big) \tag{from (3)} \\&\ge \sum_{y_2} p(y_2)h\Big(h^{-1}\big(\sum_{y_1}p(y_1)H(X_1|y_1)\big)\ast h^{-1}\big(H(X_2|y_2)\big)\Big) \tag{Jensen’s inequality} \\&= \sum_{y_2} p(y_2)h\Big(h^{-1}\big(H(X_1|Y_1)\big)\ast h^{-1}\big(H(X_2|y_2)\big)\Big) \\&\ge h\Big(h^{-1}\big(H(X_1|Y_1)\big)\ast h^{-1}\big(H(X_2|Y_2)\big)\Big) \tag{Jensen’s inequality} \\&= h(\alpha \ast \alpha) \end{align}$$</center>  
Thus, we have that  
<center>$$I(W^-) \le 1 − h(\alpha \ast \alpha) < 1 − h(\alpha) = I(W)$$</center>  
So what we have concluded is that for every $$\delta > 0$$, there exists $$\kappa(\delta) > 0$$ such that if $$I(W) \in (\delta, 1 − \delta)$$, we have  
<center>$$\Delta(W) = {1\over 2}[I(W^+) - I(W^-) \ge \kappa(\delta) >0$$</center>  
#### **Proof of Channel Polarization**  
Given $$W$$ and $$\delta > 0$$, define$$^{[4][5]}$$  
<center>$$\begin{align} \theta_n(\delta) &:= {1\over 2^n} \#\big\{s \in \{+, −\}^n : I(W^s) \in (\delta, 1-\delta)\big\} \tag{$\#$ means the cardinality of a set} \\&=  {1\over 2^n} \sum_{s \in \{\pm\}^n} \Bbb{1}_{\{I(W^s) \in (\delta, 1-\delta])\}} \tag{$\Bbb{1}_{\{\cdot\}}=1$ if {$\cdot$} is true else $=0$} \end{align}$$</center>  
Let  
<center>$$\begin{align} \mu_n &= {1\over 2^n} \sum_{s \in \{\pm\}^n} I(W^s) \tag{e.g. $\mu_1 = {1\over 2}[I(W^+)+I(W^-)]$} \\ \nu_n &= {1\over 2^n} \sum_{s \in \{\pm\}^n} [I(W^s)]^2 \tag{e.g. $\nu_1 = {1\over 2} [I^2(W^+)+I^2(W^-)]$} \end{align}$$</center>  
<center>$$\begin{align} \mu_{n+1} &= {1\over 2^{n+1}} \sum_{s \in \{\pm\}^{n+1}} I(W^s) \\&= {1\over 2^n} \sum_{t \in \{\pm\}^n} {1\over 2} [I(W^{t+})+I(W^{t-})] \\&= {1\over 2^n} \sum_{t \in \{\pm\}^n} I(W^t) \\&= \mu_n = \mu_0 = I(W) \\ \nu_{n+1} &= {1\over 2^{n+1}} \sum_{s \in \{\pm\}^{n+1}} [I(W^s)]^2 \\&= {1\over 2^n} \sum_{t \in \{\pm\}^n} {[I(W^{t+})]^2+[I(W^{t-}]^2 \over 2} \\&= {1\over 2^n} \sum_{t \in \{\pm\}^n} [I(W^t)]^2+[\Delta(W^t)]^2 \tag{${a^2+b^2 \over 2} = ({a+b \over 2})^2+({a-b \over 2})^2$} \\&\ge \nu_n + \theta_n(\delta)\kappa(\delta)^2 \tag{definition of $\theta_n(\delta)$} \end{align}$$</center>  
The sequence $$\nu_n$$ is thus bounded and monotone and consequently convergent; in particular $$\nu_{n+1}−\nu_n$$ converges to zero. As $$\theta_n$$ is sandwiched by  
<center>$$0 \le \theta_n(\delta) \le {\nu_{n+1} - \nu_n \over \kappa(\delta)^2}$$</center>  
between two quantities both convergent to zero, we conclude  
<center>$$\lim_{n \to \infty} \theta_n(\delta) = 0, \forall\delta > 0$$</center>  
This means that for large enough $$n$$, the fraction of mediocre channels (i.e., those with symmetric capacities in $$(\delta, 1 − \delta)$$) vanishes to zero. But by preservation of mutual information, we also know that if we define  
<center>$$\alpha_n(\delta) = {1\over 2^n} \sum_{s \in \{\pm\}^n} \Bbb{1}_{\{I(W^s) \ge 1-\delta\}}$$</center>  
<center>$$\beta_n(\delta) = {1\over 2^n} \sum_{s \in \{\pm\}^n} \Bbb{1}_{\{I(W^s) \le \delta\}}$$</center>  
we automatically have  
<center>$$\lim_{n \to \infty} \alpha_n(\delta) = I(W)$$</center>  
<center>$$\lim_{n \to \infty} \beta_n(\delta) = 1 - I(W)$$</center>  
This M.Alsan and E.Telatar's proof is much simpler than the martingale convergence theorem used by Arıkan$$^{[1]}$$.
    
Reference:  
1. E. Arikan. *Channel polarization: A method for constructing capacity-achieving codes for symmetric binary-input memoryless channels*. IEEE Trans. on Information Theory, vol.55, no.7, pp.3051–3073, July 2009.  
2. A. D. Wyner and J. Ziv. *A theorem on the entropy of certain binary sequences and applications (Part I)*. IEEE Trans.Inform.Theory, vol.19, no.6, pp.769-772, Nov.1973.  
3. Abbas El Gamal and Young-Han Kim. *Network Information Theory*. Cambridge University Press. 2011.  
4. M.Alsan and E.Telatar. *A simple proof of polarization and polarization for non-stationary memoryless channels*. IEEE Trans.Info.Theory, vol.62, no.9,pp.4873-4878. 2016.  
5. Vincent Y. F. Tan. *EE5139R: Information Theory for Communication Systems:2016/7, Semester 1*. https://www.ece.nus.edu.sg/  
6. Eren Sasoglu. *Polarization and Polar Codes*. Foundations and Trends in Communications and Information Theory Vol. 8, No. 4 (2011) 259–381  


