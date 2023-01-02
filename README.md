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
  When I decided to teach myself probability theory, I felt every source I found to be not entirely rigorous. For example, the laws of large numbers attempt to prove various flavors of convergence of $S_{n}/n$ to $\mu$ where $S_{n}=\sum_{i=1}^{n}X_{i}$ and $X_{1},X_{2},\dots$ are random variables satisfying $EX_{i}=\mu$ and various other conditions. However, the addition operation of two random variables is not treated rigorously. If $X_{1}$ and $X_{2}$ are defined on different domains, then their sum should be undefined. If $X_{1}$ and $X_{2}$ are equal in distribution and have the same domain, then it should be the case that $\lp X_{1}+X_{2}\rp/2=X_{1}=X_{2}$. After searching the literature and internet, I did not find a sufficiently rigorous treatment of the addition of random variables. This post is my attempt to rebuild probability theory with a rigorous foundation.
  </p>
  <p>
    The format of this post is to walk through the major results of Rick Durrett's textbook Probability: Theory and Examples with notation that I feel to be more intuitive. Some proofs use arguments similar to proofs found in Durrett's textbook, and some proofs require additional steps. I assume that one is familiar with measure theory, e.g. as presented in Real Analysis: Modern Techniques and Their Applications by Gerald Folland.
  </p>
</body>
</html>
