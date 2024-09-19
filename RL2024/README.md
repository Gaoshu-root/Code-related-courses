### helpful materials
* [Spinning Up as a Deep RL Researcher](https://spinningup.openai.com/en/latest/spinningup/spinningup.html)


Iterate fast in simple environments (推荐的简单测试环境)： `CartPole-v0, InvertedPendulum-v0, FrozenLake-v0, and HalfCheetah-v2`

Measure everything (一些算法指标)： **the mean/std/min/max for cumulative rewards**, **episode lengths**, and **value function estimates**, along with the **losses for the objectives**, and the details of any exploration parameters (like **mean entropy** for stochastic policy optimization, or **current epsilon** for epsilon-greedy as in DQN). Also, **watch videos of your agent’s performance every now and then**.

----------

* [Reinforcement Learning Tips and Tricks](https://stable-baselines3.readthedocs.io/en/master/guide/rl_tips.html)


     |  Single Process|  Multiprocessed
-------- | -----| -----
Discrete Actions | `DQN` with extensions (double DQN, prioritized replay, …) <br>训练缓慢、但样本效率高(replay buffer) |`PPO` or `A2C`
Continuous Actions  |`SAC`, `TD3`, `CrossQ` and `TQC` |`PPO`, `TRPO` or `A2C`


