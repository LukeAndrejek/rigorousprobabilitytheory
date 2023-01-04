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
    The format of this post is to walk through the major results of Rick Durrett's textbook Probability: Theory and Examples. I introduce new notation and prove additional statements as needed. Not all results from Durrett's textbook require new notation, so I assume that one is familiar with the remaining definitions and results from the book. Some proofs use arguments similar to proofs found in the book, and some proofs require additional steps. I also assume that one is familiar with measure theory, e.g. as presented in Real Analysis: Modern Techniques and Their Applications by Gerald Folland.
  </p>
  <p>
    I also tend to include a large number of steps in the calculations in my proofs. This is simply a personal preference.
  </p>
  <h2>
    Highlights
  </h2>
  <p>
    Here I will list the important definitions and results without proofs.
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
    <ins>The \(L^{2}\) Weak Law of Large Numbers:</ins> Let \(X_{1},X_{2},\dots\) be a sequence of random variables and \(\mu\in\mathbb{R}\) such that \(EX_{i}=\mu\) for all \(i\in\mathbb{N}\) and such that \(X_{i}\odot X_{j}\) is integrable for all \(i,j\in\mathbb{N}\) with \(i\neq j\). Suppose the collection of variances \(\operatorname{var}\left(X_{i}\right)\) is bounded above by some \(C\in\mathbb{R}\). Let \(S_{n}=\oplus_{1}^{n}X_{i}\). Then \(S_{n}/n\to\mu\) in \(L^{2}\).
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
    <ins>Definition:</ins> Let \(X_{1},X_{2},\dots\) be a sequence of random variables on a probability space \(\Omega\). We say that \(X_{1},X_{2},\dots\) converges <ins>almost surely</ins> or ``a.s.'' if \(P\left(\lim_{n\to\infty}X_{n}\text{ exists}\right)=1\). We say that \(X_{1},X_{2},\dots\) converges a.s. to a random variable \(X\) on \(\Omega\) if \(P\left(\lim_{n\to\infty}X_{n}=X\right)=1\).
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
</body>
</html>
