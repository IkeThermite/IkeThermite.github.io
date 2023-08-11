---
layout: default
title:  "Dynamic Programming for American Option Pricing"
usemathjax: true
---
Please note that this post relies on [The Simple Introduction to Dynamic Programming](/2023/02/09/dynamic-programming).

## The Optimal Exercise Problem
Consider the continuous-time American option pricing problem,

$$V_t = \sup_{t^*\in\mathcal{T}}E_t^Q\bigl[\beta^{t^*-t} H(S_{t^*})\bigr]. $$

Here, $V_t$ is the current price of an American option, written on an underlying $S_t$ with payoff $H(S_t)$.

The $\beta^{ t^* -t }$ is the prevailing discount factor from the future exercise time, $t^*$, to the current time, $t$, and $\mathcal{T}$ is the set of all admissable stopping times on $[t,T]$, with $T$ the maturity of the option.

The difference between this equation and the standard risk-neutral pricing equation for European options is the presence of the supremum. It indicates that the price of the American option is determined by $t ^ { * }$, the exercise time that maximizes the present value of the option, known as the *optimal exercise time*.

Thus, this pricing equation can be considered as an *optimal decision making problem:* "Given that at each moment we can decide to either exercise or not exercise the option, what is the optimal decision policy?"

Since exercising the option terminates the sequence, this is the same as finding the optimal exercise time.

## Stochastic Optimal Control
We again consider a discrete-time grid, with a finite time-horizon corresponding to the maturity of the option, such that $t\in\{0, 1, \dots, N\}$. The points on this grid represent the times when we need choose whether to exercise the option or not.

It is important to note that because we are only considering a finite number of exercise times, we are actually valuing a *Bermudan* option. As we increase the resolution of our grid, the price will approach that of an American option.

We let our state space be the states of the underlying, such that $x_t := S_t$. In our introduction to [dynamic programming](./2023-02-09-dynamic-programming.md), we had the constraint that the next state must be a deterministic function of the current state and the action taken in the current state, i.e., $x_{t+1} = T(x_t, a_t)$. This no longer true: $S_t$ is a stochastic process. As such, $x_{t+1}=T(x_t, a_t, X_{t+1})$ where $X_{t+1}$ is a random variable at $t$. In the classical Black-Scholes-Merton environment, $X_{t+1}$ would be lognormally distributed.

The optimal decision making problem becomes

$$V(x_t) = \max_{a_s\in D(x_s)}E^Q_t\biggl[\sum_{s=t}^N\beta^{s-t}F(x_s, a_s)\biggr].$$

The conditional expectation is required because of the randomness in the state space: we can now only hope to find the policy that is optimal *in expectation*. This is a *stochastic control problem.*

## American Option Pricing
Following similar heuristics as in the deterministic case, we can arrive at the Bellman equation for stochastic control,

$$V(x_t) = \max_{a_t\in D(x_t)}\left\{F(x_t, a_t) + E^Q_t\bigl[\beta V(x_{t+1})\bigr] \right\}.$$

In the case of American option pricing, the set $D(x_t)$ only has two elements. We can either exercise the option, which we denote $a_1$, or not, which we denote $a_2$. 

If we exercise the option, we receive the payoff of the option immediately, that is $F(x_t, a_1) = H(x_t)$. However the future expectation becomes zero: after exercise, the option is worthless.

If we decide not to exercise the option, we receive no payoff right now, i.e., $F(x_t, a_2) = 0$. However, the future expectation will be non-zero.

Thus, the above equation becomes

$$V(x_t) = \max\bigl({H(x_t)}, E^Q_t\bigl[\beta V(x_{t+1})\bigr]\bigr).$$

This is the *dynamic programming equation for American options*. It says that the value of an American option at the current time, is the maximum of its *intrinsic value* (the value of immediate exercise) and its *continuation value* (the value of holding the option beyond the current time, *conditional* on the current state).