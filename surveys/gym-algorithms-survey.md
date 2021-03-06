# Algorithms for OpenAI gym

In this survey I list and give brief summary of algorithm applicable to
[OpenAI gym][gym] environments.
OpenAI gym is an open-source toolkit for developing and comparing
reinforcement learning algorithms.
There are algorithms for classic control, Atari games, Humanoid walking.

[gym]: https://github.com/openai/gym

## Cross-entropy Method

[CEM] is derivative-free optimization method.
It is evolutionary algorithm that works embarrassingly well.
The main idea of [CEM] is to maintain a distribution of possible solutions
and update this distribution at each step.
It can be applied to learn the weights of a function approximator
drawing each weight from an independent Gaussian distribution.

[cem]: http://ie.technion.ac.il/CE/files/papers/Learning%20Tetris%20Using%20the%20Noisy%20Cross-Entropy%20Method.pdf

## Deep Q-network

[DQN] is an artificial agent that can learn policies directly from
high-dimensional sensory inputs using end-to-end reinforcement learning.
Receiving only the pixels and the game score of Atari 2600 games as inputs
it is able to achieve a level comparable to human game tester across 49 games
using same network architecture and hyperparameters.

It combines reinforcement learning with deep convolutional neural networks.
Moreover it addresses the problem of learning instability by using experience
replay and iterative updates of action-values toward target values only
periodically.

[dqn]: https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf

## Deep Reinforcement Learning with Double Q-learning

[Double DQN][double-dqn] is adaptation to DQN algorithm that prevents
substantial overestimations particularly in some games in the Atari 2600 games.
Generally Q-learning is known to sometimes learn unrealistically high action
values because it includes a maximization step over estimated action values,
which tends to prefer overestimated to underestimated values.

[double-dqn]: https://arxiv.org/abs/1509.06461

## Prioritized Experience Replay

[Prioritized experience replay][prioritized] is general method that lets
online reinforcement algorithm remember and reuse past.
It can be applied to DQN which uses uniform sampling.
However, this prioritized experience so as to replay important transitions
more frequently and therefore learn more efficiently.

[prioritized]: https://arxiv.org/abs/1511.05952

## Asynchronous Advantage Actor-critic

[A3C] is method for deep reinforcement learning that uses asynchronous
gradient descent for optimization of deep neural networks.
Instead of experience replay [A3C] asynchronously executes multiple agents in
parallel on multiple instances of an environment.
This parallelism speeds up training and decorrelates the data.
Therefore it can be applied to robustly and efficiently to train a deep neural
network.

[a3c]: https://arxiv.org/abs/1602.01783

## Trust Region Policy Optimization

[TRPO] is an iterative procedure for optimizing policies with guaranteed
monotonic improvement.
It is effective for optimizing neural networks by minimizing a surrogate
objective function that guarantees policy improvement with non-trivial step
sizes.
Its [paper][trpo] shows that it can learn complex policies for swimming,
hopping, and walking, as well as playing Atari games directly from raw images.

[trpo]: https://arxiv.org/abs/1502.05477

## Proximal Policy Optimization

[PPO] methods have benefits of [TRPO] but are much simpler to implement and
have better sample complexity.
[PPO] propose a objective with clipped probability ratios which forms a
pessimistic estimate of the performance of a policy.
To optimize a policy it alternates between sampling data for the policy
and performing several epochs of optimization on the sampled data.

[ppo]: https://arxiv.org/abs/1707.06347
