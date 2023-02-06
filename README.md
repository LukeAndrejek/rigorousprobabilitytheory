# rigorousprobabilitytheory
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Rigorous Probability Theory</title>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
  <script id="MathJax-script" async
          src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>
</head>
<body>
  <h1>
    Rigorous Probability Theory
  </h1>
  <h2>
    Introduction
  </h2>
  <p>
  When I decided to teach myself probability theory, I found the notation from every source I came across to be counterintuitive. For example, if \(X_{1}\) and \(X_{2}\) are random variables defined on different domains, then their sum should be undefined. If \(X_{1}\) and \(X_{2}\) are equal in distribution and have the same domain, then it should be the case that \(\left(X_{1}+X_{2}\right)/2=X_{1}=X_{2}\). If \(X_{1},X_{2},\dots\) is a sequence of independent and identically distributed random variables, then the sum \(n^{-1}\sum_{i=1}^{n}X_{i}\), which appears e.g. in the laws of large numbers, should be equal to \(X_{i}\) for all \(i\). This post is my attempt to rebuild probability theory with more intuitive notation.
  </p>
  <p>
    I will start this post with a list of the unorthodox definitions and theorems I have developed. This provides a brief overview without digging into the weeds. Then, I will attempt to provide a comprehensive treatment of probability theory from the point of view of someone who is already familiar with measure theory, e.g. through reading Real Analysis: Modern Techniques and Their Applications by Gerald Folland. The structure will closely resemble Rick Durrett's textbook Probability: Theory and Examples. I will introduce new notation and prove additional statements as needed. While I would like this presentation of probability theory to be entirely self-contained, some of my proofs would be identical to those found in Durrett's textbook, and so in these cases I will state the result and give instructions on where to find the proof.
  </p>
  <p>
    I also tend to include a large number of steps in the calculations in my proofs. This is simply a personal preference.
  </p>
  <h2>
    Highlights
  </h2>
  <p>
    Here I will list important definitions and results that I want to discuss in this post.
  </p>
  <p>
    <ins>Definition:</ins> The <ins>probability sum</ins> of two random variables \(X_{1}\) and \(X_{2}\) defined on probability spaces \(\left(\Omega_{1},P_{1}\right)\) and \(\left(\Omega_{2},P_{2}\right)\), respectively, is a function on \(\left(\Omega_{1}\times\Omega_{2},P_{1}\times P_{2}\right)\) which we will denote by \(X_{1}\oplus X_{2}\) and define by \(\left(X_{1}\oplus X_{2}\right)\left(x_{1},x_{2}\right)=X_{1}\left(x_{1}\right)+X_{2}\left(x_{2}\right)\).
  </p>
  <p>
    <ins>Proposition:</ins> If \(X_{1}\) and \(X_{2}\) are random variables, then so is \(X_{1}\oplus X_{2}\).
  </p>
  <p>
    <ins>Definition:</ins> The <ins>probability product</ins> of two random variables \(X_{1}\) and \(X_{2}\) defined on probability spaces \(\left(\Omega_{1},P_{1}\right)\) and \(\left(\Omega_{2},P_{2}\right)\), respectively, is a function on \(\left(\Omega_{1}\times\Omega_{2},P_{1}\times P_{2}\right)\) which we will denote by \(X_{1}\odot X_{2}\) and define by \(\left(X_{1}\odot X_{2}\right)\left(x_{1},x_{2}\right)=X_{1}\left(x_{1}\right)\cdot X_{2}\left(x_{2}\right)\).
  </p>
  <p>
    <ins>Proposition:</ins> If \(X_{1}\) and \(X_{2}\) are random variables, then so is \(X_{1}\odot X_{2}\).
  </p>
  <p>
    <ins>The \(L^{2}\) Weak Law of Large Numbers:</ins> Let \(X_{1},X_{2},\dots\) be a sequence of random variables and \(\mu\in\mathbb{R}\) such that \(EX_{i}=\mu\) for all \(i\in\mathbb{N}\) and such that \(X_{i}\odot X_{j}\) is integrable for all \(i,j\in\mathbb{N}\) with \(i\neq j\). Suppose the set \(\left\lbrace\operatorname{var}\left(X_{i}\right):i\in\mathbb{N}\right\rbrace\) is bounded above by some \(C\in\mathbb{R}\). Let \(S_{n}=\oplus_{1}^{n}X_{i}\). Then \(S_{n}/n\to\mu\) in \(L^{2}\).
  </p>
  <p>
    <ins>Definition:</ins> We say that random variables \(X_{1},X_{2},\dots\) <ins>converge in probability</ins> to \(\mu\) if for all \(\varepsilon>0\) we have \(P_{n}\left(\left\lbrace\left|X_{n}-\mu\right|\geq\varepsilon\right\rbrace\right)\to 0\) as \(n\to\infty\).
  </p>
  <p>
    <ins>The Probability Weak Law of Large Numbers:</ins> Let \(X_{1},X_{2},\dots\) be a sequence of random variables and \(\mu\in\mathbb{R}\) such that \(EX_{i}=\mu\) for all \(i\in\mathbb{N}\) and such that \(X_{i}\odot X_{j}\) is integrable for all \(i,j\in\mathbb{N}\) with \(i\neq j\). Suppose the set \(\left\lbrace\operatorname{var}\left(X_{i}\right):i\in\mathbb{N}\right\rbrace\) is bounded above by some \(C\in\mathbb{R}\). Let \(S_{n}=\oplus_{1}^{n}X_{i}\). Then \(S_{n}/n\to\mu\) in probability.
  </p>
  <p>
    <ins>The Weak Law of Large Numbers:</ins> Let \(X\) be a random variable such that \(E\left|X\right|<\infty\) and if \(X_{n}=X\mathbb{1}_{X^{-1}\left[-n,n\right]}\), then \(\forall i,j\in\mathbb{N}\), \(X_{i}\odot X_{j}\) is integrable. Let \(S_{n}=\bigoplus_{1}^{n}X\) and \(\mu=EX\). Then \(S_{n}/n\to\mu\) in probability.
  </p>
  <p>
    <ins>Definition:</ins> Let \(X_{1},X_{2},\dots\) be a sequence of random variables on a probability space \(\Omega\). We say that \(X_{1},X_{2},\dots\) converges <ins>almost surely</ins> or "a.s." if \(P\left(\lim_{n\to\infty}X_{n}\text{ exists}\right)=1\). We say that \(X_{1},X_{2},\dots\) converges a.s. to a random variable \(X\) on \(\Omega\) if \(P\left(\lim_{n\to\infty}X_{n}=X\right)=1\).
  </p>
  <p>
    <ins>Theorem:</ins> Given probability spaces \(\left(\Omega_{1},M_{1},P_{1}\right),\left(\Omega_{2},M_{2},P_{2}\right),\dots\), there exists a unique probability measure \(P=\times_{1}^{\infty}P_{i}\) on \(M=\bigotimes_{1}^{\infty}M_{i}\) such that, for every \(A\in M\) of the form \(A=\times_{1}^{\infty}A_{i}\), we have \(P\left(A\right)=\prod_{1}^{\infty}P_{i}\left(A_{i}\right)\).
  </p>
  <p>
    <ins>The Strong Law of Large Numbers:</ins> Let \(X\) be a random variable on \(\Omega\) with \(E\left|X\right|<\infty\). Set \(EX=\mu\) and \(S_{n}=\bigoplus_{1}^{n}X\). Let \(\varphi_{n}\) be defined such that for any function \(f_{n}\) on \(\times_{1}^{n}\Omega\) and any point \(\omega=\left(\omega_{1},\omega_{2},\dots\right)\in\times_{1}^{\infty}\Omega\), we have \(\varphi_{n}\left(f_{n},\omega\right)=f_{n}\left(\omega_{1},\dots,\omega_{n}\right)\). Then \(\varphi_{n}\left(S_{n}/n\right)\to\mu\) a.s. with respect to the measure \(P=\times_{1}^{\infty}P_{i}\).
  </p>
  <h2>
    Random Variables
  </h2>
  <p>
    <ins>Definition:</ins> A <ins>probability space</ins> consists of \(\left(\Omega,\mathscr{F},P\right)\) where \(\Omega\) is some measurable set, \(\mathscr{F}\) is a \(\sigma\)-algebra on \(\Omega\), and \(P:\mathscr{F}\to\left[0,1\right]\) is a <ins>probability measure</ins>, which means that it is a measure on \(\Omega\) such that \(P\left(\Omega\right)=1\).
  </p>
  <p>
    <ins>Definition:</ins> Given a probability space \(\left(\Omega,\mathscr{F},P\right)\), a <ins>random variable</ins> is an \(\left(\mathscr{F},P\right)\)-measurable function \(X:\Omega\to\mathbb{R}\). If the range of \(X\) is an arbitrary measurable space \(\left(S,\mathscr{S}\right)\), then we call \(X\) a <ins>random element</ins> of \(\left(S,\mathscr{S}\right)\). \(X\) is associated with a probability measure on \(\mathbb{R}\) referred to as its <ins>distribution</ins> and defined by \(\mu\left(A\right)=P\left(X\in A\right)=P\left(X^{-1}\left(A\right)\right)=P\left(\left\lbrace\omega\in\Omega:X\left(\omega\right)\in A\right\rbrace\right)\). \(X\) is also associated with a <ins>distribution function</ins> \(F:\mathbb{R}\to\left[0,1\right]\) given by \(F\left(x\right)=P\left(X\leq x\right)=P\left(X^{-1}\left(\left(-\infty,x\right]\right)\right)=P\left(\left\lbrace\omega\in\Omega:X\left(\omega\right)\leq x\right\rbrace\right)\).
  </p>
  <p>
    <ins>Example:</ins> Random variables can be used to model random events. For example, suppose you flip two coins, and then you get 2 dollars for every head and lose 1 dollar for every tail. We can model this using a random variable \(X\) where \(\Omega=\left\lbrace HH,HT,TH,TT\right\rbrace\), \(\mathscr{F}\) is the power set of \(\Omega\), and \(P\) is defined so that \(P\left(\omega\right)=0.25\) for every \(\omega\in\Omega\). Then we set \(X\left(TT\right)=-2\), \(X\left(HT\right)=X\left(TH\right)=1\), and \(X\left(HH\right)=4\).
  </p>
  <p>
    <ins>Definition:</ins> If a random variable \(X\) is integrable with respect to a probability measure \(P\), then the <ins>expected value</ins> of \(X\) is denoted \(E\left(X\right)\) or \(EX\) and equal to \(\int_{\Omega}X\,dP\).
  </p>
  <h2>
    Addition of Random Variables
  </h2>
  <p>
    We will define the addition of random variables in a way that matches our intuition behind real world applications of the law of large numbers. For example, let \(X\) be a random variable representing a coin flip: \(\Omega=\left\lbrace H,T\right\rbrace\), \(P\left(H\right)=P\left(T\right)=1/2\), \(X\left(T\right)=0\), and \(X\left(H\right)=1\). Given any \(\varepsilon>0\), let \(P_{n}\) denote the probability that after flipping \(n\) coins, the total number of heads divided by \(n\) is within \(\varepsilon\) of \(1/2\). One of the weak laws of large numbers should prove that \(P_{n}\) converges to \(1\) as \(n\to\infty\). To prove this statement, we need to combine multiple coin flips in some way. For example, we need to combine \(X\) with itself to obtain a new random variable that we interpret as the outcome of two coin flips. The resulting random variable should have domain \(\left\lbrace TT,TH,HT,HH\right\rbrace\) and assign \(0\) to \(TT\), \(1\) to \(TH\) and \(HT\), and \(2\) to \(HH\). This example motivates our definition.
  </p>
  <p>
    <ins>Definition:</ins> The <ins>probability sum</ins> of two random variables \(X_{1}\) and \(X_{2}\) defined on probability spaces \(\left(\Omega_{1},P_{1}\right)\) and \(\left(\Omega_{2},P_{2}\right)\), respectively, is a function on \(\left(\Omega_{1}\times\Omega_{2},P_{1}\times P_{2}\right)\) which we will denote by \(X_{1}\oplus X_{2}\) and define by \(\left(X_{1}\oplus X_{2}\right)\left(x_{1},x_{2}\right)=X_{1}\left(x_{1}\right)+X_{2}\left(x_{2}\right)\).
  </p>
  <p>
    Using this definition, the laws of large numbers can be rephrased as the convergence of \(n^{-1}\bigoplus_{1}^{n}X_{i}\) to \(EX_{i}\) in some sense.
  </p>
  <p>
    <ins>Theorem:</ins> If \(X_{1}\) and \(X_{2}\) are random variables, then so is \(X_{1}\oplus X_{2}\).
  </p>
  <p>
    <ins>Proof:</ins> By definition, \(\left(P_{1}\times P_{2}\right)\left(X_{1}\oplus X_{2}\right)
=P_{1}\left(X_{1}\right)P_{2}\left(X_{2}\right)=1\). We will prove that \(X_{1}\oplus X_{2}\) is measurable when \(X_{1}\) and \(X_{2}\) are indicator, then simple, then measurable functions.
  </p>
  <p>
    For indicator functions, suppose \(X_{1}=a\mathbb{1}_{B}\) and \(X_{2}=c\mathbb{1}_{D}\). Then \(\left(X_{1}\oplus X_{2}\right)\left(\omega_{1},\omega_{2}\right)
=a\mathbb{1}_{B}\left(\omega_{1}\right)+c\mathbb{1}_{D}\left(\omega_{2}\right)\). Given a set \(S\) and a condition \(x\), define a set \(\delta_{x}\left(S\right)=\emptyset\) if \(x\) is false and \(\delta_{x}\left(S\right)=S\) if \(x\) is true. Then for each measurable \(S\subset\mathbb{R}\),
    \[
    \begin{aligned}
    \left(X_{1}\oplus X_{2}\right)^{-1}\left(S\right)
    =&
    \delta_{a\in S}
    \left(X_{1}^{-1}\left(B\right)\times X_{2}^{-1}\left(D^{c}\right)\right)
    \cup
    \delta_{c\in S}
    \left(X_{1}^{-1}\left(B^{c}\right)\times X_{2}^{-1}\left(D\right)\right)
    \\
    &\cup
    \delta_{a+c\in S}
    \left(X_{1}^{-1}\left(B\right)\times X_{2}^{-1}\left(D\right)\right)
    \cup
    \delta_{0\in S}
    \left(X_{1}^{-1}\left(B^{c}\right)\times X_{2}^{-1}\left(D^{c}\right)\right).
    \end{aligned}
    \]
Each of the sets in the above union are measurable since \(X_{1}\) and \(X_{2}\) are measurable functions. Thus \(\left(X_{1}\oplus X_{2}\right)^{-1}\left(S\right)\) is a countable union of measurable sets and thus is measurable.
  </p>
  <p>
    For simple functions, suppose \(X_{1}=\sum_{1}^{n}a_{i}\mathbb{1}_{B_{i}}\) and \(X_{2}=\sum_{1}^{m}c_{j}\mathbb{1}_{D_{j}}\), so that \(\left(X_{1}\oplus X_{2}\right)\left(\omega_{1},\omega_{2}\right)
=\sum_{i,j}a_{i}\mathbb{1}_{B_{i}}\left(\omega_{1}\right)+c_{j}\mathbb{1}_{D_{j}}\left(\omega_{2}\right)\). Let \(B=\bigcup_{1}^{n}B_{i}\) and \(D=\bigcup_{1}^{m}D_{j}\). Then for any measurable \(S\),
    \[
    \begin{aligned}
    \left(X_{1}\oplus X_{2}\right)^{-1}\left(S\right)
    =&
    \bigcup_{i=1}^{n}
    \delta_{a_{i}\in S}
    \left(X_{1}^{-1}\left(B_{i}\right)\times X_{2}^{-1}\left(D^{c}\right)\right)
    \\
    &\cup
    \bigcup_{j=1}^{m}
    \delta_{c_{j}\in S}
    \left(X_{1}^{-1}\left(B^{c}\right)\times X_{2}^{-1}\left(D_{j}\right)\right)
    \\
    &\cup
    \bigcup_{i,j}
    \delta_{a_{i}+c_{j}\in S}
    \left(X_{1}^{-1}\left(B_{i}\right)\times X_{2}^{-1}\left(D_{j}\right)\right)
    \\
    &\cup
    \delta_{0\in S}
    \left(X_{1}^{-1}\left(B^{c}\right)\times X_{2}^{-1}\left(D^{c}\right)\right).
    \end{aligned}
    \]
This is again a countable union of measurable sets and thus is measurable.
  </p>
  <p>
    If \(X_{1},X_{2}\) are measurable, then we know by Theorem 2.10 of Folland's analysis textbook that there are sequences of simple functions \(X_{1,n}\) and \(X_{2,n}\) such that \(X_{1,n}\to X_{1}\) and \(X_{2,n}\to X_{2}\). Then \(X_{1,n}\oplus X_{2,n}\) are simple (and thus measurable) functions which converge pointwise to \(X_{1}\oplus X_{2}\). We also know by Proposition 2.7 from the same book that if a sequence of measurable functions converge pointwise, then their limit is measurable. Thus \(X_{1}\oplus X_{2}\) is measurable, which confirms that it is a random variable. \(\square\)
  </p>
  <p>
    It will sometimes be useful in our calculations to change variables using the following proposition.
  </p>
  <p>
    <ins>Proposition:</ins> Let \(X:\Omega\to S\) be a random element of \(\left(S,\mathscr{S}\right)\) with distribution \(\mu\left(A\right)=P\left(X^{-1}\left(A\right)\right)\). If \(f\) is measurable from \(\left(S,\mathscr{S}\right)\) to \(\left(\mathbb{R},\mathscr{R}\right)\) such that \(f\geq 0\) or \(\int_{\Omega}\left|f\circ X\right|\,dP<\infty\), then \(\int_{\Omega}f\circ X\,dP
=\int_{S}f\,d\mu\).
  </p>
  <p>
    <ins>Proof:</ins> This is Theorem 1.6.9 in Durrett's textbook, so you can find the proof there. By the way, "\(\mu\left(dy\right)\)" is synonymous with "\(d\mu\)" in his proof.
  </p>
  <p>
    <ins>Note:</ins> We may use the notation \(d\mu\left(x\right)\) when integrating a function with input \(x\) with respect to the measure \(\mu\). For example, \(\int f\left(x\right)\,d\mu\left(x\right)=\int f\,d\mu\).
  </p>
  <p>
    The following theorem shows us how to compute the distribution function of a probability sum.
  </p>
  <p>
    <ins>Theorem:</ins> Let \(X_{1},X_{2}\) be random variables with distribution functions \(F_{1},F_{2}\). Let \(\mu_{i}\left( A\right)=P_{i}\left( X_{i}\in A\right)=P_{i}\left(\left\lbrace\omega\in\Omega_{i}:X_{i}\left(\omega\right)\in A\right\rbrace\right)\) for each Borel set \(A\subset\mathbb{R}\). Then \(X_{1}\oplus X_{2}\) has distribution function
    \[
    \begin{aligned}
    F\left( x\right)
    &=
    \left( P_{1}\times P_{2}\right)
    \left(\left\lbrace
    \left(\omega_{1},\omega_{2}\right)\in\Omega_{1}\times\Omega_{2}:
    X_{1}\left(\omega_{1}\right)+X_{2}\left(\omega_{2}\right)\leq x
    \right\rbrace\right)
    \\
    &=
    \int_{\mathbb{R}}
    F_{1}\left( x-x_{2}\right)
    \,d\mu_{2}\left( x_{2}\right)
    \\
    &=
    \int_{\mathbb{R}}
    F_{2}\left( x-x_{1}\right)
    \,d\mu_{1}\left( x_{1}\right)
    .
    \end{aligned}
    \]
  </p>
  <p>
    <ins>Proof:</ins> We will prove the first integral formula as the second follows by symmetry. Let \(A_{x}=\left\lbrace\left(\omega_{1},\omega_{2}\right)\in\Omega_{1}\times\Omega_{2}:X_{1}\left(\omega_{1}\right)+X_{2}\left(\omega_{2}\right)\leq x\right\rbrace=\left( X_{1}\oplus X_{2}\right)^{-1}\left(\left( -\infty,x\right]\right)\). Then \(\left(\omega_{1},\omega_{2}\right)\in A_{x}\) iff \(X_{1}\left(\omega_{1}\right)\leq x-X_{2}\left(\omega_{2}\right)\). Therefore,
    \[
    \begin{aligned}
    F\left( x\right)
    &=
    \left( P_{1}\times P_{2}\right)\left( A_{x}\right)
    \\
    &=
    \int_{\Omega_{1}\times\Omega_{2}}
    \mathbb{1}_{A_{x}}\left(\omega_{1},\omega_{2}\right)
    \,d\left( P_{1}\times P_{2}\right)
    \\
    &=
    \int_{\Omega_{2}}\int_{\Omega_{1}}
    \mathbb{1}_{A_{x}}\left(\omega_{1},\omega_{2}\right)
    \,dP_{1}\left(\omega_{1}\right)
    \,dP_{2}\left(\omega_{2}\right)
    \\
    &=
    \int_{\Omega_{2}}
    P_{1}\left( A_{x}\left(\omega_{1},\omega_{2}\right)\right)
    \,dP_{2}\left(\omega_{2}\right)
    \\
    &=
    \int_{\Omega_{2}}
    P_{1}\left\lbrace\left(\omega_{1}\in\Omega_{1}:X_{1}\left(\omega_{1}\right)\leq x-X_{2}\left(\omega_{2}\right)\right\rbrace\right)
    \,dP_{2}\left(\omega_{2}\right)
    \\
    &=
    \int_{\Omega_{2}}
    F_{1}\left( x-X_{2}\left(\omega_{2}\right)\right)
    \,dP_{2}\left(\omega_{2}\right)
    \\
    &=
    \int_{\mathbb{R}}
    F_{1}\left( x-x_{2}\right)
    \,d\mu\left( x_{2}\right)
    .
    \end{aligned}
    \]
Note that we have used Fubini's Theorem, which applies because \(X_{1}\oplus X_{2}\) is measurable, and so \(A_{x}=\left( X_{1}\oplus X_{2}\right)^{-1}\left(\left(-\infty,x\right]\right)\) is measurable. Also, between the final two equations, we used the change of variables formula with \(f\left( y\right)=F_{1}\left( x-y\right)\).
  </p>
  <p>
    It is not always clear how to integrate with respect to the measure \(\mu_{1}\) and \(\mu_{2}\) above, so we explore this further.
  </p>
  <p>
    <ins>Definition:</ins> Let \(f:S_{1}\to S_{2}\) be measurable from \(\left( X_{1},\mathscr{S}_{1}\right)\) to \(\left( X_{2},\mathscr{S}_{2}\right)\), and let \(\nu_{1}\) be a measure on \(X_{1}\). Then there is a measure \(\nu_{2}\) on \(X_{2}\) such that \(\forall B\in\mathscr{S}_{2}\), \(\nu_{2}\left( B\right)=\nu_{1}\left( f^{-1}\left( B\right)\right)\). \(\nu_{2}\) is called a <ins>pushforward</ins> of \(\nu_{1}\) and is sometimes denoted \(\nu_{2}=f\#\nu_{1}\).
  </p>
  <p>
    <ins>Theorem:</ins>
Given the data from the above definition, if \(g:S_{2}\to S_{3}\) is measurable, then \(g\) is integrable w/r/t \(\nu_{2}\) iff \(g\circ f\) is integrable w/r/t \(\nu_{1}\), and in this case we have
    \[
    \begin{aligned}
        \int_{S_{2}}g\,d\nu_{2}
        =
        \int_{f^{-1}\left( S_{2}\right)}
        g\circ f\,d\nu_{1}
        .
    \end{aligned}
    \]
  </p>
  <p>
    <ins>Proof:</ins> According to Wikipedia, this appears as a theorem in Bogachev's "Measure Theory" textbook. I plan to include the full proof here eventually.
  </p>
  <p>
    The following theorem gives us a slightly easier formula for computing distribution functions for probability sums.
  </p>
  <p>
    <ins>Theorem:</ins> Let \(F_{1},F_{2}\) be distribution functions. For \(\omega\in\left( 0,1\right)\), define \(X_{i}\left(\omega\right)=\sup\left(\left\lbrace y:F_{i}\left( y\right)<\omega\right\rbrace\right)\) for \(i=1,2\) (by Theorem 1.2.2 in Durrett's textbook, \(X_{i}\) is a random variable whose distribution function is \(F_{i}\)). Let \(\mu_{i}\left( A\right)=P_{i}\left( X_{i}\in A\right)\) for each Borel set \(A\subset\mathbb{R}\). Let \(m\) be the Lebesgue measure on \(\mathbb{R}\). Then \(X_{1}\oplus X_{2}\) has distribution function
    \begin{aligned}
        F\left( x\right)
        &=
        \int_{\mathbb{R}}
        F_{1}\left( x-x_{2}\right)
        \,d\mu_{2}\left( x_{2}\right)
        =
        \int_{0}^{1}
        F_{1}\left( x-X_{2}\left( x_{2}\right)\right)
        \,dm\left( x_{2}\right)
        \\
        &=
        \int_{\mathbb{R}}
        F_{2}\left( x-x_{1}\right)
        \,d\mu_{1}\left( x_{1}\right)
        =
        \int_{0}^{1}
        F_{2}\left( x-X_{1}\left( x_{1}\right)\right)
        \,dm\left( x_{1}\right)
        .
    \end{aligned}
  </p>
  <p>
    <ins>Proof:</ins> As before, we will only prove
    \begin{aligned}
        F\left( x\right)
        &=
        \int_{\mathbb{R}}
        F_{1}\left( x-x_{2}\right)
        \,d\mu_{2}\left( x_{2}\right)
        =
        \int_{0}^{1}
        F_{1}\left( x-X_{2}\left( x_{2}\right)\right)
        \,dm\left( x_{2}\right)
    \end{aligned}
    as the remaining equalities follow by symmetry. We have previously proven the first equality above. For the second equality, we know that \(F_{1}\left( x-x_{2}\right)\) is integrable w/r/t \(\mu_{2}\), and so we can apply the previous theorem with \(f=X_{2}\), \(g=F_{1}\), \(S_{1}=\left( 0,1\right)\), \(S_{2}=\mathbb{R}\), \(S_{3}=\left[ 0,1\right]\), \(\nu_{1}=m\), and \(\nu_{2}=\mu_{2}\).
  </p>
<h2>
  Independence is Unnecessary
</h2>
  <p>
      The previous section is mathematically sound, but what value does it provide over the existing literature? The previous theorem allows us to partially explore this question. Its formula for the distribution function for \(X_{1}\oplus X_{2}\) is almost identical to Theorem 2.1.10 in Durrett's textbook, except that Theorem 2.1.10 gives a formula for the distribution function for \(X_{1}+X_{2}\) so long as \(X_{1}\) and \(X_{2}\) are independent. Since our theorem does not assume independence, it is reasonable to question the legitimacy of our theorem.
  </p>
  <p>
    To explore this nuance, let's first recall the definition of independence. Two events \(A\) and \(B\) are independent if \(P\left( A\cap B\right)=P\left( A\right) P\left( B\right)\). Two random variables \(X\) and \(Y\) are independent if for all Borel sets \(A,B\subset\mathbb{R}\), we have
    \[
    \begin{aligned}
        P\left( X^{-1}\left( A\right)\cap Y^{-1}\left( B\right)\right)
        =
        P\left( X^{-1}\left( A\right)\right)
        P\left( Y^{-1}\left( B\right)\right)
        .
    \end{aligned}
    \]
    Problems arise because the \(P\)'s in the above equation are abiguous. If \(X\) has domain \(\Omega_{X}\) with measure \(P_{X}\) and \(Y\) has domain \(\Omega_{Y}\) with measure \(P_{Y}\), then certainly \(P\left( X^{-1}\left( A\right)\right)=P_{X}\left( X^{-1}\left( A\right)\right)\) and \(P\left( Y^{-1}\left( B\right)\right)=P_{Y}\left( Y^{-1}\left( B\right)\right)\). When \(\Omega_{X}\neq\Omega_{Y}\) and \(P_{X}\neq P_{Y}\), then the only valid interpretation is
    \[
    \begin{aligned}
        P\left( X^{-1}\left( A\right)\cap Y^{-1}\left( B\right)\right)
        =
        P_{X\times Y}
        \left(
        X^{-1}\left( A\right)\times Y^{-1}\left( B\right)
        \right)
    \end{aligned}
    \]
    where \(P_{X\times Y}\) is the product measure of \(P_{X}\) and \(P_{Y}\) on \(\Omega_{X}\times\Omega_{Y}\). However, if \(\Omega_{X}=\Omega_{Y}\) and \(P_{X}=P_{Y}\), authors sometimes behave as if
    \[
    \begin{aligned}
        P\left( X^{-1}\left( A\right)\cap Y^{-1}\left( B\right)\right)
        =
        P_{X}
        \left(
        X^{-1}\left( A\right)\cap Y^{-1}\left( B\right)
        \right)
        .
    \end{aligned}
    \]
  </p>
  <p>
    Let's consider an example. Let \(X\) be a random variable representing a game in which you flip a coin and win $1 if it comes up heads, but you lose $1 if it comes up tails. Then \(X\) has domain \(\left\lbrace H,T\right\rbrace\) with \(X\left(H\right)=1\), \(X\left(T\right)=-1\), and \(P\left(H\right)=P\left(T\right)=0.5\). A simple example of a random variable which is not independent to \(X\) is \(Y=X\). \(X\) and \(Y\) are not independent because \(P\left(X^{-1}\left(\left\lbrace 1\right\rbrace\right)\cap Y^{-1}\left(\left\lbrace 1\right\rbrace\right)\right)=P\left(\left\lbrace X=1\right\rbrace\cap\left\lbrace Y=1\right\rbrace\right)=0.5\) because the event \(H\) has probability \(0.5\) and results in both \(X\) and \(Y\) taking on the value of \(1\). Then, since \(P\left(X=1\right)=P\left(Y=1\right)=0.5\), we have \(P\left(X=1\right)\cdot P\left(Y=1\right)=0.25\neq 0.5\), and so \(X\) and \(Y\) are not independent. However, if we want independence, we can simply define \(Y\) such that \(X\) and \(Y\) are "independent and identically distributed."
  </p>
  <p>
    So then how do most textbooks define \(X+Y\)? If \(X\) and \(Y\) are not independent, then \(X+Y\) maps \(H\) to \(2\) and \(T\) to \(-2\). That is, the "\(+\)" refers to pointwise addition. But if \(X\) and \(Y\) are independent, then \(X+Y=X\oplus Y\) as we have defined previously. Therefore, in most textbooks, the addition operator is overloaded. This is one of my objections to the standard treatment of probability theory. I think it would be more intuitive and less confusing to use "\(+\)" for pointwise addition and "\(\oplus\)" when combining the outcomes of two random variables. In addition to resolving the addition overloading, this removes the need to define independence for random variables, as \(X\oplus Y\) is defined to ensure that \(P_{X\times Y}\left(X^{-1}\left( A\right)\times Y^{-1}\left( B\right)\right)=P_{X}\left(X^{-1}\left(A\right)\right)\cdot P_{Y}\left(Y^{-1}\left(B\right)\right)\).
  </p>
</body>
</html>
