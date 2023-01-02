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
  When I decided to teach myself probability theory, I found the notation from every source to be counterintuitive. For example, if \(X_{1}\) and \(X_{2}\) are random variables defined on different domains, then their sum should be undefined. If \(X_{1}\) and \(X_{2}\) are equal in distribution and have the same domain, then it should be the case that \(\left(X_{1}+X_{2}\right)/2=X_{1}=X_{2}\). If \(X_{1},X_{2},\dots\) is a sequence of independent and identically distributed random variables, then the sum \(n^{-1}\sum_{i=1}^{n}X_{i}\), which appears e.g. in the Weak Law of Large Numbers, should be equal to \(X_{i}\) for all \(i\). After searching the literature and internet, I did not find a treatment of the addition of random variables which made sense to me. This post is my attempt to rebuild probability theory with more intuitive notation.
  </p>
  <p>
    The format of this post is to walk through the major results of Rick Durrett's textbook Probability: Theory and Examples. I only discuss proofs which require new notation, so I assume that one is familiar with the remaining definitions and results from Durrett's textbook. Some proofs use arguments similar to proofs found in the textbook, and some proofs require additional steps. I assume that one is also familiar with measure theory, e.g. as presented in Real Analysis: Modern Techniques and Their Applications by Gerald Folland.
  </p>
  <h2>
    Addition of Random Variables
  </h2>
  <p>
    We will define the addition of random variables in a way that matches our intuition behind the real world implications of the law of large numbers. For example, let \(X\) be a random variable representing a coin flip: \(\Omega=\left{H,T\right}\), \(P\left(H\right)=P\left(T\right)=1/2\), \(X\left(T\right)=0\), and \(X\left(H\right)=1\). The law of large numbers should prove, among other types of convergence, that for any \(\varepsilon>0\), the probability that the total number of heads divided by \(n\) is within \(\varepsilon\) of \(1/2\) converges to \(1\) as \(n\to\infty\).
  </p>
  In this example, we would interpret \(X+X\) as the outcome of two coin flips. So the resulting random variable would have domain \(\left{TT,TH,HT,HH\right}\) and assign \(0\) to \(TT\), \(1\) to \(TH\) and \(HT\), and \(2\) to \(HH\). This example motivates our definition.
  <p>
    <ins>Definition:</ins> The <ins>probability sum</ins> of two random variables \(X_{1}\) and \(X_{2}\) on \(\left(\Omega_{1},P_{1}\right)\) and \(\left(\Omega_{2},P_{2}\right)\) is a function on \(\left(\Omega_{1}\times\Omega_{2},P_{1}\times P_{2}\right)\) which we will denote by \(X_{1}\oplus X_{2}\) and define by \(\left(X_{1}\oplus X_{2}\right)\left(x_{1},x_{2}\right)=X_{1}\left(x_{1}\right)+X_{2}\left(x_{2}\right)\).
  </p>
  <p>
    Using this definition, the law of large numbers can be rephrased as the convergence of \(n^{-1}\bigoplus_{1}^{n}X_{i}\) to \(EX_{i}\).
  </p>
</body>
</html>
