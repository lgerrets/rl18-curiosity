# Large-Scale Study of Curiosity-Driven Learning

* [arXiv](https://arxiv.org/pdf/1808.04355.pdf)
* [implementations](https://github.com/openai/large-scale-curiosity)
* [demo](https://www.youtube.com/watch?v=l1FqtAHfJLI)

## TLDR

* Curiosity-driven learning (with no extrinsic rewards) show some alignment between intrinsic and extrinsic rewards.
* Random feature representation are good for many environments but inverse dynamics shows better generalization capabilities from one environment to another close one.
* Direct error-based curiosity can be tricked by very simple stochastic environments.

This large-scale study does not go much into the details of the employed algorithms, and is rather a direct follow-up to their previous paper `D. Pathak, P. Agrawal, A. A. Efros, and T. Darrell. Curiosity-driven exploration by self-supervised
prediction. In ICML, 2017.`.

## Aim

They aimed at showing demonstrations of their previous algorithm on a large benchmark of environments including games from the Atari suite, physic-based games, etc... They also compared their previous *inverse dynamics* approach of feature representation to 3 other representations (1 of which is also learnable).

They also gave interesting an overview over the related works and approaches of intrinsic rewards: predicion errors, visitation counts, ...

## Methods

No new methods are presented in this paper.

## Technical details

All the experiments use 128 parallel agents (except for Mario: up to 2048) to collect data, which was proven to improve the gradient estimation of PPO.

Some insightful technical details are shortly given in section 2.2. 

## Experiments - results

Experiments were conducted in 54 environments: 48 Atari games, Mario, multi-player Pong, 2 Unity mazes, 2 Roboschool tasks. 

The best agent explored 11 levels of Mario using only intrinsic rewards.

Without any extrinsic rewards, 2 agents played Pong against other, resulting in the emulator crashing before one of the agent lost.

## My thoughts and takeaways

There is no significant best feature representation among the 4 presented ones. As explained in a short discussion, none of them have the 3 properties *compact*, *sufficient* and *stable*. Random features and inverse dynamics appear to be the best ones, as mentionned in **TLDR**. 

No explicit mention is made of bandits as visitation counts based approaches.

In addition to their 2017 paper, they refer to `D. Pathak, P. Mahmoudieh, G. Luo, P. Agrawal, D. Chen, Y. Shentu, E. Shelhamer, J. Malik, A. A. Efros,
and T. Darrell. Zero-shot visual imitation. In ICLR, 2018.` as a study of fine-tuning methods.

Their study on random feature representation could be related to `Yuri Burda, Harrison Edwards, Amos J. Storkey & Oleg Klimov (2018). Exploration by Random Network Distillation. CoRR, abs/1810.12894.`.

## Top Figures


## Metadata

```
@article{DBLP:journals/corr/abs-1808-04355,
  author    = {Yuri Burda and
               Harrison Edwards and
               Deepak Pathak and
               Amos J. Storkey and
               Trevor Darrell and
               Alexei A. Efros},
  title     = {Large-Scale Study of Curiosity-Driven Learning},
  journal   = {CoRR},
  volume    = {abs/1808.04355},
  year      = {2018},
  url       = {http://arxiv.org/abs/1808.04355},
  archivePrefix = {arXiv},
  eprint    = {1808.04355},
  timestamp = {Sun, 02 Sep 2018 15:01:55 +0200},
  biburl    = {https://dblp.org/rec/bib/journals/corr/abs-1808-04355},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

Tags: curiosity motivation prediction error Intrinsic Random Variational Autoencoders VAE inverse dynamics benchmark Atari Mario Pong Unity Roboschool fine-tuning generalization stochastic boredom
