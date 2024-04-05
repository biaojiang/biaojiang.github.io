---
layout: post
title:  "Machine learning and AI frameworks and resources!"
# date:   2018-07-17 11:56:00 +0100
date:   2024-04-05 11:00:00 +0200
categories: data-science
math: false
---

## ML/AI Frameworks

### Python ML/AI frameworks
* [TensorFlow](https://www.tensorflow.org)

TensorFlow was developed by Google Brain team AI researchers and engineers, supporting CPUs, GPUs, TPUs. Google's proprietary TPU is the future AI computing platform. So, for long-term considerations, TensorFlow is the best choice for ML and DL.
 
* [PyTorch](https://pytorch.orgturi)

Being supported by Facebook, PyTorch has good compatibility with Numpy, and it provides strong tensor computations and dynamic neural networks in Python with strong GPU accelerations.

| Feature | TensorFlow | PyTorch |
|---|---|---|
| Learning Curve | 🚀 More difficult | 🚀 Easier |
| Performance | ⚡ More performant | ⚡ Less performant |
| Expressiveness | 💨 Less expressive | 💨 More expressive |
| Deployment | 💪 Better for production | 🤼 Good for research and development |
| Community | 👥 Larger and more active | 👨‍💻 Smaller and growing |
| Use Cases | 🏭 Production-oriented | 👩‍🔬 Research and development |

* [Flax]

[Flax] is a neural network library built on top of [JAX], which is a high-performance Python library designed for numerical computation and machine learning with features:

1. Automatic differentiation: Simplifies calculating gradients, crucial for training neural networks.
1. Vectorization: Speeds up computations by operating on entire arrays at once.
1. Just-In-Time (JIT) compilation: Optimizes code for specific hardware, leading to significant performance gains.

So, [JAX]'s JIT compilation and [Flax]'s efficient use of [JAX] lead to fast training times. The cons is that both of these are less mature ecosystems, but it is worth exploring.

### Golang ML frameworks
* [mlpack]

It is a fast, lightweight header-only C++ machine learning library that aims to provide fast, extensible implementations of cutting-edge machine learning algorithms. It depends only on the **Armadillo** linear algebra library and the **cereal** serialization library.

 It has Golang, Python, R and Julia bindings, it is a good choice for data scientists who need to deploy machine learning models to production.

One test case is [Iris dataset classification and visualization][GoML].

### Rust ML frameworks
* [Candle][Candle]

[Candle][Candle] is a minimalist machine learning framework for Rust with a focus on performance (including GPU support) and ease of use. It aims to provide a performant and user-friendly alternative to existing Python-based machine learning frameworks for developers who prefer **Rust**'s syntax and performance benefits.

One use case is [MINST classification][CandleMinst].

### Cloud AI platforms
* GCP [Vertex AI][VertexAI]
* [Azure Machine Learning][AzureML]

## Phased out frameworks
As the field of ML/AI evolves, new techniques and algorithms are being developed all the time. If a framework is not able to keep up with these new developments, it will become less competitive and less useful for solving real-world problems.
* [Turi Create][turicreate]

Turi Create was sponsored by Apple, if familiar with Mac OS, then Turi Create is much easier to code and export models to CoreML for use in iOS, macOS, watchOS, and tvOS apps. It has been archived since **2020**.

* [tensorflow_macos][tensorflowMacos]

It was also archived by Apple, it only supports TensorFlow up to v2.5.

It is important to be aware of the potential **risks** of using a framework that is not actively developed or that is not compatible with the latest versions of the software that you depend on.


## Databases for Training

* [kaggle](https://www.kaggle.com/datasets)
* [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.html)
* [BigQuery public database][BigQuery]

## NLP and Generative AI Resources
* [ChatGPT][ChatGPT]
* [Meta AI Llama 2][Llama2]
* [Google Gemini][gemini]
* [Google Bard][bard]

To solve real problems, we must combine using these LLM tools, as each tool has strengths and weaknesses.

## NLP and LLM Training and Deployment
[huggingface][huggingface] is to democratize good machine learning. They offer a variety of tools and resources for machine learning, including models, datasets, and spaces, specifically in NLP and LLM re-training and model sharing.

Here are some of the specific things that Hugging Face does:

* Provide a platform for sharing and using machine learning models. This platform, called Transformers Hub, allows developers to upload their models and share them with others. It also makes it easy for users to find and use models that are relevant to their needs.

* Develop and maintain a number of open-source machine learning libraries such as Transformers and Datasets.

* Host a number of events and workshops about machine learning. These events are a great way for developers to learn about new techniques and tools, and to network with other people in the field.

Overall, Hugging Face is a valuable resource for anyone who is interested in machine learning. They are committed to making machine learning more accessible and easier to use, and they are making a real difference in the field.

## Related Paper Searching

* [Google Scholar](https://scholar.google.se)
* [arxiv-sanity](https://www.arxiv-sanity.com)

## Impacts of ML/AI on Industry 
ML and AI are rapidly transforming industries across the globe, bringing about significant changes and impacting various aspects of business operations. From healthcare to finance, manufacturing to retail, the applications of ML/AI are becoming increasingly pervasive, driving innovation and enhancing efficiency.

Here are some specific examples of how ML/AI is impacting industries:

- Manufacturing:

1. Predictive maintenance algorithms for preventing equipment breakdowns
1. AI-powered quality control for identifying and resolving defects in real-time
1. ML-driven supply chain optimization for reduced costs and improved efficiency
1. Shop floor overall equipment effectiveness (OEE) optimization

- Healthcare:

1. AI-powered diagnostics for early disease detection
1. ML-driven drug discovery for accelerated drug development
1. Personalized medicine for tailored treatment plans

- Finance:

1. AI-powered trading algorithms for optimized investment decisions
1. ML-driven fraud detection for secure financial systems, especially for _cryptocurrency_ blockchain scam detection and tracking
1. Smart chatbots for 24/7 customer support
1. AI-powered credit scoring for informed lending decisions

- Retail:

1. AI-powered recommendation engines for personalized product suggestions
1. ML-driven demand forecasting for optimized inventory levels
1. Chatbots for personalized customer support
1. AI-powered pricing strategies for maximizing revenue

### Industrial insights on ML/AI
#### [Industrial Careers in the Age of Machine Learning][teguar]

ML/AI can improve our daily life efficiency, e.g., we can use [Google SGE, generative AI in Search][SGELab] to summarize this article by [TEGUAR][teguar] as the following:

* This article looks at the impact of machine learning on the industrial sector. It explains the different types of machine learning, including supervised, unsupervised, and reinforcement learning.

* Machine learning is already being used in a variety of ways in the industrial sector, including predictive maintenance, predictive quality, and employee training.

* As machine learning becomes more common, it will lead to changes in the types of jobs available and the skills needed to perform them.





[turicreate]: https://github.com/apple/turicreate
[tensorflowMacos]: https://github.com/apple/tensorflow_macos
[VertexAI]: https://cloud.google.com/vertex-ai
[AzureML]: https://azure.microsoft.com/en-us/products/machine-learning
[ChatGPT]: https://openai.com/chatgpt
[Llama2]: https://ai.meta.com/llama/
[gemini]: https://www.gemini.com/
[bard]: https://bard.google.com/
[huggingface]: https://huggingface.co/
[BigQuery]: https://cloud.google.com/bigquery
[Candle]: https://github.com/huggingface/candle/
[mlpack]: https://www.mlpack.org/
[GoML]: https://plotsignal.com/data-science/2022/12/27/plotlib-in-go.html
[CandleMinst]: https://x.com/biajia/status/1711375014136529292?s=20
[teguar]: https://teguar.com/industrial-careers-in-the-age-of-machine-learning/
[SGELab]: https://labs.google.com/search?authuser=0&source=srp&is=ag
[JAX]: https://jax.readthedocs.io/en/latest/
[Flax]: https://flax.readthedocs.io/en/latest/
