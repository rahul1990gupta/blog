Title: Why you can't run llamma locally
Date: 2024-10-20 10:20
Category: Software Engineering
Slug: local-llamma
Authors: Rahul Gupta
Summary:  Since the release of LLaMA to the public, more capable LLMs from companies like Meta, Mixtral, and others have become available, often matching the performance of OpenAI's models. Thanks to market competition, model weights are generally accessible to anyone with an internet connection.

<img src="{static}/images/llamma.jpg">

Before we address the question, let's first understand what is required to train and run a large language model (LLM).

1. Model Weights: Since the release of LLaMA to the public, more capable LLMs from companies like Meta, Mixtral, and others have become available, often matching the performance of OpenAI's models. Thanks to market competition, model weights are generally accessible to anyone with an internet connection.

2. Deep Learning Libraries: While TensorFlow and PyTorch are excellent general-purpose deep-learning frameworks, they introduce significant overhead when running LLM models. These models barely fit into memory, necessitating custom, lightweight model loaders for consumer hardware. Much work is currently underway to address this issue.

3. Hardware: Most companies use Nvidia datacenter-grade GPUs for training and running these models. These chips are extremely expensive and inaccessible to all but well-funded VC-backed startups.

How Can We Truly Democratize AI?
The first significant effort in this direction was the development of llama.cpp, a single C++ file that could run the LLaMA model on a CPU, with support for M1/M2 chips. This innovation allowed people to run LLM models on their machines without needing to purchase $20,000 Nvidia A100 chips. However, it did not support Nvidia and AMD GPUs. Many software solutions (like Ollama) that run LLaMA models use this in the backend.

Next came Tinygrad from George Hotz, backed by $6 million in funding. His goal is to build a deep learning library capable of running LLMs on various devices, including:

- Consumer Nvidia GPUs

- Consumer AMD GPUs

- Apple M-series hardware

- All Intel CPUs

- Qualcomm Snapdragon X Elite chips

The architecture of this deep learning framework is designed to easily add more drivers as needed.

Another approach by [Andrej Karpathy](https://twitter.com/karpathy) involves writing low-level C code to train the GPT-2 family of models. This approach sacrifices some functionality and flexibilities but gains significant performance.

Here is how Andrej Karapathy compared the [two frameworks](https://twitter.com/karpathy/status/1783527854741114981))

It's worth clarifying that the llm.c repo and Tinygrad repo are very different kinds of projects. Both aim to train LLMs quickly. Tinygrad aspires to be an actual compiler (think: gcc), taking high-level descriptions of arbitrary networks and compiling them to run efficiently on different backends. llm.c, on the other hand, is more like a direct, assembly-level program, written by hand, for a very specific, narrow program (the GPT-2 training loop). Unlike typical assembly programs, you get something low-level but still readable. Compilers may match or surpass the runtime but producing readable code is not usually their goal.

llama.cpp was great for running llama model on cpu, running large model at usable latency requires leveraging all hardware availble to the user. And both these projects are aiming for that.

Conclusion
The goal of these projects is to return LLM capabilities to the hands of end-users by allowing them to run on consumer-grade hardware. With unified chips, increased RAM, and improved deep learning libraries, we may soon be able to run LLMs on smartphones.