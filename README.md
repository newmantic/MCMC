# MCMC


The Markov Chain Monte Carlo (MCMC) method is a class of algorithms used to sample from a probability distribution. When direct sampling is difficult, MCMC allows us to approximate the distribution by generating a sequence of samples that form a Markov chain.


A Markov chain is a sequence of random variables X_1, X_2, X_3, ... where the probability of moving to the next state depends only on the current state. This is known as the Markov property:
P(X_(n+1) = x | X_n = x_n, X_(n-1) = x_(n-1), ..., X_1 = x_1) = P(X_(n+1) = x | X_n = x_n)
The chain is said to have a stationary distribution if, as n increases, the distribution of X_n converges to a fixed distribution, regardless of the initial state.

The Monte Carlo method involves using randomness to solve problems that might be deterministic in principle. In MCMC, we generate random samples from a probability distribution and use these samples to approximate the distribution.

The basic idea behind MCMC is to construct a Markov chain that has the desired distribution pi(x) as its stationary distribution. By running the chain for a long time, the samples generated will approximate samples from pi(x).


One of the most commonly used MCMC methods is the Metropolis-Hastings algorithm.

Initialization:
Start with an initial value X_0 for the Markov chain.

Proposal Distribution:
At each step n, propose a new state Y using a proposal distribution q(Y | X_n), which suggests a candidate for the next state based on the current state.

Acceptance Probability:
Calculate the acceptance probability alpha as:
alpha = min( 1, (pi(Y) * q(X_n | Y)) / (pi(X_n) * q(Y | X_n)) )
pi(x) is the target distribution, and q(x | y) is the proposal distribution.

Accept or Reject:
Generate a random number u from a uniform distribution U(0, 1).
If u <= alpha, accept the new state Y and set X_(n+1) = Y.
If u > alpha, reject Y and set X_(n+1) = X_n.

Repeat:
Repeat the process to generate a sequence of samples X_1, X_2, ..., X_n.

The Metropolis-Hastings algorithm constructs a Markov chain whose stationary distribution is the target distribution pi(x). After running the algorithm for a sufficient number of iterations (known as the burn-in period), the samples X_n can be used to approximate pi(x).


Time Complexity
The efficiency of the Metropolis-Hastings algorithm depends on the choice of the proposal distribution and the number of iterations. Generally, the time complexity is proportional to the number of iterations needed to achieve convergence.
