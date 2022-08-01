# BNN
The Documentation of me studying for BNN

## Introduction 

- Elementary process unit in the central nervous system are neurons. 
- Neuron has three distinct parts:
  - Dendrites, input device and transmits them to the soma 
  - Soma, non linear CPU of Neuron, if the the total Input exceeds a threshold than an Output is generated  
  - and axon, transfers the output to the next neurons.
- The junction between two neurons is called synapse. 
- Presynapic cell - sending neuron 
- Postsynapic cell - receiving neuron 

### Spike trains 

The signal of a neuron consists of a short electrical pulse, with an amplitude of about $100$ $mV$ and a duration of $1-2$ $ms$. A chain of action potentials emitted by a single neuron is calles a spike train. The form of theses action potential does not carry any information. What we track is the number and timing of spikes. 
After a transmition to the axon the neuron enters a so called refractory period, where it is difficult to excite the action potential. 

## Elements of Neuronal Dynamics 

We measure the potential difference between the interior of the cell and its surroundings and denote this function with $u(t)$. Without any input the the neuron is at rest with a constant membrane potential $u_{rest}$. 

### Postsynaptic Potentials 

We want to model the time course $u(t)$ of the neuron $i$. Before the input spike arrives, we have $u_i(t) = u_{rest}$. Lets say at time $t=0$ the presynaptic neuron $j$ fires its spike. For $t>0$, the response from neuron $i$ is

$$
\begin{align}
  u(t) - u_{rest} =: \epsilon_{ij}(t)
\end{align}
$$

If $\epsilon_{ij}(t)$ is positive (negative) we have an excitatory (inhibitory) neuron. 

### firing Threshold and Action Potential 

Consider two presynaptic neurons $j = 1,2$, which both send spikes to the postsynaptic neuron $i$. Neuron $j=1$ fires spikes at $t_1^{(1)},t_1^{(2)}, \dots$, similarly neuron $j=2$ fire at  $t_1^{(2)},t_1^{(2)}, \dots$. Each spike evokes a postsynaptic potential $\epsilon_{i1}$ or $\epsilon_{i1}$, respectively. Since we have a small number of neurons we can approximate the sum by 

$$
\begin{align}
  u_i(t) = \sum_j \sum_s \epsilon_{ij} (t - t_j^{(s)}) + u_{rest}
\end{align}
$$

i.e., the membrane potential responds linearly to input spikes. This linearity breaks if the membrane potential reaches the threshold. After that the amplitude rises to about $100$ $mV$, and from there it drops lower than the resting potential $u_{rest}$ (hyperpolarization). 

## First Lecture 
The first lecture begins with the basic mathematical model, that is we will measure the spkie times that arrive at the neurons, e.g. 

#### The current pules $I_{\Delta t }(t):$
$$
\begin{align}
  \int_{-\infty}^{\infty}I_{\Delta t}(t) dt = q
\end{align}
$$

with $I_{\Delta t}(t) = \frac{q}{\Delta t} 1_{(0,\Delta t)}(t)$
