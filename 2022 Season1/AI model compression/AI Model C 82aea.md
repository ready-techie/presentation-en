# AI Model Compression
### 👀 Script ( From now on, I'll try to present without a script)

---
![Screen Shot 2022-03-09 at 22.23.44.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.23.44.png)

hello, i’m dragon.

let’s talk about AI model Compression.

![Screen Shot 2022-03-09 at 22.24.12.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.24.12.png)

Now, the AI industry is developing rapidly and huge.

However, compared to the advancement of technology, there are only a few cases in which AI services has been applied to devices around us.

Because in the process of making the developed AI model an AI service,  they encountered several problems, including limited hardware performance, compatibility issues, and network delays.

![Screen Shot 2022-03-09 at 22.25.10.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.25.10.png)

In this presentation,  i will talk about AI model compression, one of the technologies to solve these problems.

![Screen Shot 2022-03-09 at 22.25.45.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.25.45.png)

first, what is a Artificial Neural Network?

# 1. **Aritificial Neural Network**

AI Model Compression is a technology that converts artificial neural networks light and fast.

Here, an artificial neural network is technology that mimics a biologicial neural network in our brain by conneting artificially created neurons on a computer.

And the artificial neural network is composed of layers of neurons.

How does the artificial neural network work?

The artificial Neural network sequentially transmits electronic signals from each floor to the next floor along the pre-learned Neural network structure and outputs predicted information.

![Screen Shot 2022-03-09 at 22.26.18.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.26.18.png)

In general, Artificial Neural networks go through two main precesses.

## 1. Training

Training is the process of teaching AI models using collected data.

By repeatedly showing the data, the neural network trains patterns on the predicted value.

Training is usually divided into supervised learning and unsupervised learning.

Supervised learning is the process of finding patterns with a teacher.

Unsupervised learning is the process of finding and learning patterns alone.

![Screen Shot 2022-03-09 at 22.26.58.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.26.58.png)

Here is a simple example about training

The training process is like simulation.

Through simulation, various cat data are learned in the artificial neural network.
Fat cats, black cats, striped cats, and other various cat data to be used in the real service.

If these data are repeatedly learned in the artificial neural network, the artificial neural network will have the intelligence to find cats.

![Screen Shot 2022-03-09 at 22.27.21.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.27.21.png)

## 2. Inference

Inference means making predictions based on the trained knowledge of the artificial neural network.

Through inference, we can use artificial neural networks in AI services.

For reference, even if new information comes in the inference process, the artificial neural network doesn’t learn new information.

because inference is the process of predicting answers based on pre-learned AI model.

![Screen Shot 2022-03-09 at 22.27.35.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.27.35.png)

Here is a simple example about inference

Q : What kind of animal is this?

A : It’s a Cat! 😸

![Screen Shot 2022-03-09 at 22.27.54.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.27.54.png)

# 2. **What is AI model compression?**

Then, why do we need AI model compression and what are they used for?

The most important part of AI model services is The inference process.

If you have developed an AI model with high accuracy by training good data to an AI model for a long time.
However, if the model has delays and a lot of computaion in the inference process, the model can’t be an AI service.

Therefore, in the AI model development process, there are various technologies that efficiently make the inference process, such as quantization, pruning, and Batch Folding.

![Screen Shot 2022-03-09 at 22.28.20.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.28.20.png)

Currently, many AI models have delays and a lot of computation.

Therefore, the inference process is performed on the GPU and TPU located in the cloud.

However, the use of AI compression technology makes AI model faster and reduces the amount of computation.

This means that the AI model can perform the inference process on embedded devices with limited hardware performance and CPU with low computational power.

The inference process in the cloud can be directly executed on smartphones and edge devices that are close to us.

Therefore, we will be able to experience many AI models as services in our daily life.

![Screen Shot 2022-03-09 at 22.28.31.png](AI%20Model%20C%2082aea/Screen_Shot_2022-03-09_at_22.28.31.png)

😸