# Prompt-Engineering-Guide

Prompt engineering is a relatively new discipline for developing and optimizing prompts to efficiently use language models (LMs) for a wide variety of applications and research topics. Prompt engineering skills help to better understand the capabilities and limitations of large language models (LLMs).

Prompt engineering is not just about designing and developing prompts. It encompasses a wide range of skills and techniques that are useful for interacting and developing with LLMs. It's an important skill to interface, build with, and understand capabilities of LLMs. You can use prompt engineering to improve safety of LLMs and build new capabilities like augmenting LLMs with domain knowledge and external tools.

## Introduction

### LLM Settings
When designing and testing prompts, you typically interact with the LLM via an API. You can canfigure a few parameters to get different results for your prompts. Tweaking these settings are important to improve reliability and desirability of response and it takes a bit of experimentation to figure out the proper settings for your use cases.

**temperature** \
In short, the lower the `temperatur`, the more deterministic the result in the sense that the highest probable next token is always picked. Increasing temperature could lead to more randomness, which encourages more diverse or creative outputs. You are essentially increasing the weights of the other possible tokens. In terms of application, you might want to use a lower temperature value for tasks like fact-based QA to encourage more factual and concise responses. For poem generation or other creative tasks, it might be beneficial to increase the temperature value.

**Top P** \
A sampling technique with temperature, called nucleus sampling, where you can control how deterministic the model is. If you are looking for exact and factual answers keep this low. If you are looking for more diverse responses, increase to a higher value. If you use Top P it means that only the tokens comparising the `top_p`  probability mass are considered for responses, so a low `top_p` value selects the most confident responses. This means that a high `top_p` value will enable the model to take a look at more possible words, including less likely ones, leading to more diverse outputs. \
The general recommendation is to alter temperature or Top_p but not both.

**Max Length** \
You can manage the number of tokens the model generates by adjusting the `max length`. Specifying a max length helps you prevent long or irrelevant responses and control costs.

**Stop Sequences** \
A `stop sequences` is a string that stops the model from generating tokens. Specifying stop sequence is another way to control the lengthand structure of the model's response.

**Frequency Penalty** \
The `frequency penalty` applies a penalty on the next token proportional to how many times that token already appeared in the response and prompt. The higher the frequency penalty, the less likely a word will a word will appear again. This setting reduces the repetition of words in the model's response by giving tokens that appear more a higher penalty.

**Presence Penalty** \
The `presence penalty` also applies a penalty on repeated tokens but, unlike the frequency penalty, the penalty is the same for all repeated tokens. A token that appears twice and a token that appears 10 times are penalized the same. This setting prevents the model from repeating phrases too often in its response. If you want to model to generate diverse or creative text, you might want to use a higher presence penalty. Or, if you need the model to stay focused, try using a lower presence penalty.

Similar to `temperature` and `top_p`, the general recommendation is to alter the frequency or presence penalty but not both.
