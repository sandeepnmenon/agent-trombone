# Results

The results for the letter A
<audio controls>
  <source src="{{ site.baseurl }}/audio/correct_letter_A.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>
![letter_A]({{ site.baseurl }}/images/letter_A_spect.png)

Model output after 100K iterations
<audio controls>
  <source src="{{ site.baseurl }}/audio/generated_from_mi_model_1.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>
![letter_A_100K]({{ site.baseurl }}/images/letter_A_spect_100K.png)

Model output after 1M iterations
<audio controls>
  <source src="{{ site.baseurl }}/audio/generated_from_mi_model_best.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>
![letter_A_1M]({{ site.baseurl }}/images/letter_A_spect_1M.png)

## Learnings from experiments 

![ep_rew_mean]({{ site.baseurl }}/images/ep_rew_mean.png)

In the early stages of training (around 0 to 200k steps), there are significant fluctuations. This is expected behavior as the agent is initially exploring the environment and trying to learn an optimal policy. 

The graph also shows periods where the average episodic reward is negative, which suggests that the agent is receiving penalties from the environment during these episodes. However, after approximately 300k steps, the graph seems to stabilize and converge. This indicates that the agent has learned a policy that consistently achieves positive rewards in the environment, and its performance has reached a relatively stable state.

![explained_variance]({{ site.baseurl }}/images/explained_variance.png)

The explained variance graph shows very low values, close to zero, throughout the training process. A low explained variance indicates that the value function is struggling to accurately predict the expected returns or discounted cumulative rewards from the sampled trajectories.

![value_loss]({{ site.baseurl }}/images/value_loss.png)

The value function seems to be performing poorly, which can hinder the agent's learning process and lead to inefficient policy updates. A high value loss indicates that the value function is not accurately predicting the expected returns, which aligns with the low explained variance observed above.

![policy_gradient]({{ site.baseurl }}/images/policy_gradient.png)

The policy gradient loss graph exhibits a decreasing trend initially, which is a desirable behavior. However, it appears to stabilize at a relatively high value towards the end of the training process. A high policy gradient loss suggests that the policy updates are still significant, and the agent is struggling to converge to an optimal policy. This could be due to the inaccurate value function, as discussed earlier, or other factors such as a complex environment or poorly shaped reward function.

