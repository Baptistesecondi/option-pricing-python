# Derivatives Pricing: Vanilla and Barrier Options

A Python implementation and cross-validation of three independent option pricing methods — closed-form **Black-Scholes**, **Monte Carlo simulation**, and **finite-difference PDE schemes** (explicit and Crank-Nicolson) — applied to European vanilla options and single-barrier options (knock-in / knock-out).

The goal of this project was to build each pricing method from first principles, then use them to check each other: put-call parity, barrier in-out parity, and cross-method agreement (Monte Carlo vs. finite differences vs. closed-form) are used throughout as consistency checks rather than taken for granted.

## What's inside

- **Closed-form Black-Scholes** pricing and Greeks (Delta, Gamma, Vega, Theta, Rho)
- **Monte Carlo** pricing of vanilla options, with convergence analysis and 95% confidence intervals
- **Monte Carlo** pricing of barrier options (down/up, in/out), simulated on a discrete monitoring grid and vectorized in memory-bounded chunks so both path count and monitoring frequency can be pushed high without blowing up memory
- **Finite differences (explicit scheme)** for vanilla and barrier options, including a demonstration of the scheme's numerical instability when the time step is too large relative to the spatial step
- **Finite differences (Crank-Nicolson scheme)**, unconditionally stable, for both vanilla and barrier options
- A study of each finite-difference scheme's **order of convergence** in time (first-order explicit vs. second-order Crank-Nicolson), isolated from spatial discretization error
- An example of a real discretization pitfall: for a barrier close to the spot price, the Monte Carlo discrete-monitoring bias decays much more slowly than for a barrier further away, and needs a substantially finer monitoring grid to become negligible — illustrated directly in the notebook rather than glossed over

## Getting started

```bash
pip install -r requirements.txt
jupyter notebook Option_Pricing_Vanilla_Barrier.ipynb
```

The notebook runs end-to-end in under three minutes on a standard laptop.

## Structure

Everything lives in a single notebook, `Option_Pricing_Vanilla_Barrier.ipynb`, organized into numbered sections that build up from payoffs to closed-form pricing, then Monte Carlo, then finite differences, with cross-checks between methods along the way.

## Next steps

A companion project (in progress) extends this framework beyond Black-Scholes to stochastic and local volatility models (Heston, Dupire) and to path-dependent structured payoffs such as autocallables.

## Author

Baptiste Secondi — [LinkedIn](https://linkedin.com/in/baptiste-secondi-a6168832b)
