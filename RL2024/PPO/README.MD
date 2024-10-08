
>算法： PPO-Clip
>1：输入：策略的初始参数 $\theta_0$，价值函数的初始参数     $\phi_0$
>2：${\bf for} ~ k=0,1,2,\dots~ {\bf do}$：<font color=blue>每个回合</font>
3：$~~~~~~$通过在环境中运行策略 $\pi_k=\pi(\theta_k)$ 收集轨迹集 ${\cal D}_k=\{\tau_i\}~~~~~$ <font color=blue> $|{\cal D}_k|$ 个并行 actors，每个 actor 收集 长度为 $T$ 个时间步 的数据</font>
4：$~~~~~~$计算奖励 (rewards-to-go) $\hat R_t~~~~~$ <font color=blue> $\hat R_t=\sum\limits_{t^\prime=t}^TR(s_{t^\prime},a_{t^\prime},s_{t^\prime +1})$</font>  [【参考链接】](https://spinningup.openai.com/en/latest/spinningup/rl_intro3.html)$~~~~~$ <font color=blue> $R(\tau)=\sum\limits_{t=0}^\infty \gamma^tr_t$</font> [【参考链接】](https://spinningup.openai.com/en/latest/spinningup/rl_intro.html)
5：$~~~~~~$计算优势估计，基于当前价值函数 $V_{\phi_k}$ 的 $\hat A_t$ (使用任何优势估计方法)$~~~~~$<font color=blue>GAE</font>
>>![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fd2fc632a57848f6847fda9deef3a17e.png =400x)
>
>6：$~~~~~~$通过最大化 PPO-Clip 目标 更新策略：
$~~~~~~~~~~~$
$~~~~~~~~~~~\theta_{k+1}=\arg\max\limits_\theta\frac{1}{|{\cal D}_k|T}\sum\limits_{\tau\in{\cal D}_k}\sum\limits_{t=0}^T\min\Big(\frac{\pi_{\theta} (a_t|s_t)}{\pi_{\theta_k}(a_t|s_t)}A^{\pi_{\theta_k}}(s_t,a_t),g(\epsilon,A^{\pi_{\theta_k}}(s_t,a_t))\Big)$
$~~~~~~~~~~~$
$~~~~~~~~~~~$![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3ba2bd7046ce408880590633b487f54f.png =250x)
$~~~~~~~~~~~$一般 随机梯度上升 + Adam 
7：$~~~~~~$均方误差**回归 拟合 价值函数**:
$~~~~~~~~~~~$
$~~~~~~~~~~~\phi_{k+1}=\arg \min\limits_\phi\frac{1}{|{\cal D}_k|T}\sum\limits_{\tau\in{\cal D}_k}\sum\limits_{t=0}^T\Big(V_\phi(s_t)-\hat R_t\Big)^2$
$~~~~~~~~~~~$
$~~~~~~~~~~~$一般 梯度下降
8：$\bf end ~for$

