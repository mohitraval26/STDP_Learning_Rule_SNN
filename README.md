# STDP_Learning_Rule_SNN

## Introduction
Traditional ANNs have seen great success, but face challenges in computation and
biological realism. SNNs, with spiking communication and bio-inspired learning,
offer promising alternatives. STDP, mirroring synaptic strengthening or weakening
seen in biological neurons, is a particularly appealing learning rule for SNNs.

## Scope
This project will serve as a Proof of Concept for a new learning rule inspired by
biological mechanisms, specifically building on Hebb's postulate and Spike-Timing
Dependent Plasticity (STDP). This involves implementing an algorithm that mimics
how biological neurons strengthen connections based on firing patterns. It also
involves analyzing how the STDP rule affects the network's behavior by observing
how weights change over time and how the network responds to different input
patterns.

## Maths
In the preprocessing stage, the Iris dataset is loaded, normalized, and flattened.
Using the TimedArray method, the dataset is converted into spike trains, with
each data point represented by spikes at 0.1ms intervals.
Next, in network definition, neuron behaviors are defined using the Leaky
Integrate-and-Fire (LIF) model, while connections between neurons are
established using Brian2's Synapses class. Parameters such as time constants,
thresholds, and initial synaptic weights are set.
The LIF model is represented by the equation:

$$\tau \cdot \frac{dv}{dt} = I - v$$

Where,
𝜏 is the membrane time constant
𝑣 represents the membrane potential
𝐼 represents the input current

Spike-Timing Dependent Plasticity (STDP) is implemented by defining equations
for pre-synaptic and post-synaptic weight dynamics within the Synapses class. The
synaptic weights are updated based on pre and post-synaptic activity using
specific functions. The spike traces are defined by the equations:

$$\tau_{pre} \cdot \frac{d a_{pre}}{dt} = -a_{pre}$$

$$\tau_{post} \cdot \frac{d a_{post}}{dt} = -a_{post}$$

On a pre-synaptic spike, the weights are then updated as:

$$a_{pre} = a_{pre} + A_{pre}$$
$$w = w + a_{post}$$

Similarly on a post-synaptic spike, the weight are updated as:

$$a_{post} = a_{post} + A_{post}$$
$$w = w + a_{pre}$$

apre and apost are the spike traces which govern the change of weights in the
network.

In the simulation phase, the model is run for a specified duration using
b2.run(duration). StateMonitor objects record membrane voltages and synaptic
states, while SpikeMonitor objects record spike times of neurons.

Subsequently, the recorded data is analyzed to understand network dynamics,
including firing rates of neurons and the evolution of synaptic weights under STDP.
Finally, a comparison is made by training a Convolutional Neural Network (CNN)
model on the same dataset, recording execution times, and comparing the time
taken for STDP in SNN with Forward and Backward Propagation in CNN.

## Results
This project demonstrate the effectiveness of the developed Spiking Neural
Network (SNN) model with Spike-Timing Dependent Plasticity (STDP) compared to
a traditional Convolutional Neural Network (CNN) on the Iris dataset.

Analysis reveals dynamic firing rates and synaptic weight evolution in the SNN,
showcasing its biological realism.

Spike times and membrane voltages offer insights into neuron activations and
STDP-driven plasticity.

Execution time comparison between SNN with STDP and CNN demonstrated the
computational efficiency of the SNN approach. The comparison captured in the
form of graphs is as follows:

CNN

![image](https://github.com/user-attachments/assets/43e98cb7-156d-4771-9cec-11877b9fa663)

SNN

![image](https://github.com/user-attachments/assets/68f5850b-8a8b-4af4-a6bf-d1967646b4d6)







