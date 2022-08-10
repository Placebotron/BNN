Safe state 

# BNN
The Documentation of me studying for BNN

## Introduction 

- Elementary process unit in the central nervous system are neurons. 
- Neuron has three distinct parts:
  - Dendrites, input device and transmits them to the soma 
  - Soma, non linear CPU of Neuron, if the the total Input exceeds a threshold than an output is generated  
  - and axon, transfers the output to the next neurons
- The junction between two neurons is called synapse
- Presynapic cell - sending neuron 
- Postsynapic cell - receiving neuron 

### Spike trains 

The signal of a neuron consists of a short electrical pulse, with an amplitude of about $100$ $mV$ and a duration of $1-2$ $ms$. A chain of action potentials emitted by a single neuron is calles a spike train. The form of theses action potential does not carry any information. What we track is the number and timing of spikes. 
After a transmition to the axon the neuron enters a so called refractory period, where it is difficult to excite the action potential. 

## Elements of Neuronal Dynamics 

We measure the potential difference between the interior of the cell and its surroundings and denote this function with $u(t)$. Without any input the the neuron is at rest with a constant membrane potential $u_{rest}$. 

### Postsynaptic Potentials 

We want to model the time course $u(t)$ of the neuron $i$. Before the input spike arrives we have $u_i(t) = u_{rest}$. Lets say at time $t=0$ the presynaptic neuron $j$ fires its spike. For $t>0$, the response from neuron $i$ is

$$
\begin{align}
  u_i(t) - u_{rest} =: \epsilon_{ij}(t)
\end{align}
$$

If $\epsilon_{ij}(t)$ is positive (negative) we have an excitatory (inhibitory) neuron. 

### Firing Threshold and Action Potential 

Consider two presynaptic neurons $j = 1,2$, which both send spikes to the postsynaptic neuron $i$. Neuron $j=1$ fires spikes at $t_1^{(1)},t_1^{(2)}, \dots$, similarly neuron $j=2$ fire at  $t_2^{(1)},t_2^{(2)}, \dots$. Each spike evokes a postsynaptic potential $\epsilon_{i1}$ or $\epsilon_{j1}$, respectively. Since we have a small number of neurons we can approximate the sum by 

$$
\begin{align}
  u_i(t) = \sum_j \sum_s \epsilon_{ij} (t - t_j^{(s)}) + u_{rest}
\end{align}
$$

i.e., the membrane potential responds linearly to input spikes. This linearity breaks if the membrane potential reaches the threshold. After that the amplitude rises to about $100$ $mV$, and from there it drops lower than the resting potential $u_{rest}$ (hyperpolarization). 

## Integrate-And-Fire Models 

Since we are not trying to interprete the shape of the spkies, hence the information that is stored in it, but rather just the presence and absence of them, we reduce our model to detect events. This approach is called 'Integrate-and-Fire' model. 
For that we need two ingredients: 
- First an equation that describes the evolution of the membrane potential $u_i(t)$, (Differential equations)
- and second, a mechanism to generate spikes, (stochastic term, e.g. poission process).

So lets get started with the first one..... Differential equation enters the chat. 

### Integrate of Inputs 

The soma is surrounded by a cell membrane which is a good, but not perfect insulator. When we inject a current pulse $I(t)$ into the neuron, the additional electrical charge $q = \int I(t^{\prime}) dt^{\prime}$ has to go somewhere. That is, it will charge the cell membrane. 
Henceforth, we can see the cell membrane as a leaky capacitor, with capacity $C$ and finite resistance $R$. 


### Integrate of Inputs 

#### Analysing the Input currents 

We can split the input current into two components,

$$
\begin{align}
  I(t) = I_R + I_C
\end{align}
$$

The first component is the resistive current $I_R$ which passes through the linear resistor $R$. We can calculate is using Ohm's fucking law as $I_R = \frac{u_R}{R}$ where $u_R = u - u_{rest}$ is the voltage of the resistor, usually depending on $t$. 
The second of is the charge of the capacitor $I_C$. From its definition we can calculate it as $C=\frac{q}{u}$ and $I_C = \frac{dq}{dt} = C\frac{du}{dt}$. Thus

$$
\begin{align}
  I(t) = \frac{u(t) - u_{rest}}{R} + C\frac{du}{dt}.
\end{align}
$$

Multiplying this equation by $R$ while introducing the time constant $\tau_m = RC$ of the leaky integrator yields,

$$
\begin{align}
  \tau_m \frac{du}{dt} = -[u(t) - u_{rest}] + RI(t).
\end{align}
$$

Where we define $u$ as the membrane potential and $\tau_m$ as the membrane time constant of the neuron. 

And there we go! We introduced our first Differential equation and so far I think it is safe to say, that nothing is particularly difficult to understand. One important fact about DE is their solutions, since without a proper solution they are not for any use. 

So waht is that ominous solution 🧐













## First Lecture 
The first lecture begins with the basic mathematical model, that is we will measure the spkie times that arrive at the neurons, e.g. 

#### The current pulse $I_{\Delta t }(t):$
$$
\begin{align}
  \int_{-\infty}^{\infty}I_{\Delta t}(t) dt = q
\end{align}
$$

with $I_{\Delta t}(t) = \frac{q}{\Delta t} 1_{(0,\Delta t)}(t)$

### Membrane Potential 
$$
\begin{align}
  \tau_m \frac{dV}{dt} &= -V + V_{rest} +RI_{\Delta t}(t) \\
  V(0^-) &= V_{rest}
\end{align}
$$

### Maximum of $V(t)$
$$
\begin{align}
  O(\Delta t) &= V_{rest} + \int_0^{\Delta t} \frac{1}{\tau_m} \exp(-\frac{\Delta -s}{\tau_m}) R \frac{q}{\Delta t} ds \\ 
  &= \frac{R_q}{\Delta t}(1 - \exp(- \frac{\Delta t}{\tau_m}))
\end{align}
$$

### Important case: short pulses
&&
\begin{align}
  \Delta V := V(\Delta t) - V_{rest} = \frac{Rq}{\tau_m} + O((\frac{\Delta t}{\tau_m})^2 \frac{\Delta t}{\tau_m} \to 0
\end{align}
&&

&&
\begin{align}
  \lim_{\Delta t \to 0^+} \Delta V = \lim_{\Delta t \to 0^+} \int{- \infty}^{\Delta t} \frac{R}{\tau_m} \exp(- \frac{\Delta - s}{\tau_m}) I_{\Delta t}(s) ds= q \frac{R}{\Delta t} ds
\end{align}
&&

