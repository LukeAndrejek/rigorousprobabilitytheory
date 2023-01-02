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
  When I decided to teach myself probability theory, I found the notation from every source to be counterintuitive. For example, if \(X_{1}\) and \(X_{2}\) are random variables defined on different domains, then their sum should be undefined. If \(X_{1}\) and \(X_{2}\) are equal in distribution and have the same domain, then it should be the case that \(\left(X_{1}+X_{2}\right)/2=X_{1}=X_{2}\right). If \(X_{1},X_{2}\) is a sequence of independent and identically distributed random variables, then the sum \(n^{-1}\sum_{i=1}^{n}X_{i}\), which appears e.g. in the Weak Law of Large Numbers, should be equal to \(X_{i}\) for all \(i\). After searching the literature and internet, I did not find a treatment of the addition of random variables which made sense to me. This post is my attempt to rebuild probability theory with more intuitive notation.
  </p>
  <p>
    The format of this post is to walk through the major results of Rick Durrett's textbook Probability: Theory and Examples. I only discuss proofs which require new notation, so I assume that one is familiar with the remaining definitions and results from Durrett's textbook. Some proofs use arguments similar to proofs found in the textbook, and some proofs require additional steps. I assume that one is also familiar with measure theory, e.g. as presented in Real Analysis: Modern Techniques and Their Applications by Gerald Folland.
  </p>
</body>
</html>
