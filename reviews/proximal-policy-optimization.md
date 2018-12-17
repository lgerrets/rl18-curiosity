# Proximal Policy Optimization Algorithms


> [arvix](https://arxiv.org/abs/1707.06347)


## TLDR

* Proximal policy optimization (PPO) is a family of policy optimization methods that use multiple epochs of stochastic gradient ascent to perform each policy update.

## Aim

* Develop a method that is as stable and reliable as trust-region methods (TRPO) but that is much simpler to implement and have better overall performance.

## Methods

A PPO algorithm can be done in an actor-critic fashion where:
* each actor runs the previous iteration policy for $$T$$ timesteps
* each actor estimates the advantage functions at $$T$$ timesteps
* Then we use a surrogate loss with respect to the policy parameters using $$K$$ epochs and mini batches.

The authors propose a variety of surrogate loss functions, mainly:
  * Clipping the successive policies ratio ($$\epsilon$$ hyperparameter)
  * Run an adaptive KL scheme that changes the value of $$\beta$$ according to the KL divergence between two successive policies ($$\d_{targ}$$ hyperparameter)
  * Run a fixed KL scheme ($$\beta$$ hyperparemeter)

## Technical details

> mathematical notations, proofs

* There are no mathematical proofs per say but empirical results demonstrate the performance of PPO algorithms while their simplicity comes out naturally.

> setups

* In the experiment section, there are no parameters sharing between the policy and the value function and no entropy bonus.

> parameterizing

* To represent the policy, a fully-connected MLP with two hidden layers of 64 units, and tanh nonlinearities, outputting the mean of a Gaussian distribution, with variable standard deviations was used.


## Experiments - results

> Benchmark

* 7 simulated robotics tasks from OpenAI Gym (see the MuJoCo physics engine)
* 1 million training steps
* 3 random seeds
* Score: 
  * averaged total reward of the last 100 episodes.
  * 0: random policy score
  * 1: best result from the algorithms used.
  * average over 21 runs (3 seeds, 7 tasks) to produce a unique score per algorithm.

## My thoughts and takeaways

> pros

* Simple to implement.
* This paper provides all the ingredients for reproducibility.
* Promising results on a broad range of tasks.

> cons

* No strong theoretical guarantees: *it just happens to work!*.
* It still requires a good amount of computation!

> related stuff

## Top Figures

* Figure 3 gives an overview of several algorithms on the benchmark used in the experiments. PPO belongs consistently in the higher tier.

## Metadata

```
@article{Schulman2017ProximalPO,
  title={Proximal Policy Optimization Algorithms},
  author={John Schulman and Filip Wolski and Prafulla Dhariwal and Alec Radford and Oleg Klimov},
  journal={CoRR},
  year={2017},
  volume={abs/1707.06347}
}
```
