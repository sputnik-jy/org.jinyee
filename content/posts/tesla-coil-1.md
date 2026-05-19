---
title: "Tesla Coil 1 - The LC Circuit"
slug: "tesla-coil-1"
date: 2026-05-07T15:54:53+08:00
draft: true
summary: "A Series dedicated to the Know-How of building a Tesla Coil. EP 1: The LC Circuit"
tags: ["electronics"]
showReadingTime: true
math: true
---

## Introduction

In order to understand how Tesla Coil works, we first need to understand the fundamental circuit that makes the core of Tesla Coil - the LC Oscillator circuit.

## LC Circuit current formula derivation

### 1. KVL and Circuit Elements

Referring the series LC circuit of the diagram, Kirchoof's Voltage Law (KVL) says that the sum of the voltage drops across the inductor ($V_L$) and the capacitor ($V_C$) must equal the source voltage. 

Assuming a voltage source $V_S(t)$, we have: $ V_L(t) + V_C(t) = V_S(t) $

For an ideal inductor, the voltage drop across it is proportional to the rate of change of the current $i(t)$ flowing through it:

$$ V_L(t) = L \frac{di(t)}{dt} $$

For an ideal capacitor, the current flowing through it is proportional to the rate of change of the voltage across it, and from it we can express the voltage across the capacitor as:

$$ i(t) = C \frac{dV_C(t)}{dt} \implies V_C(t) = \frac{1}{C} \int i(t) dt $$



### 2. Formulating the Differential Equation

Substituting the expressions for $V_L(t)$ and $V_C(t)$ into the KVL equation:

$$ L \frac{di(t)}{dt} + \frac{1}{C} \int i(t) dt = V_S(t) $$

### 3. Solving the Homogeneous Equation

For a simple LC circuit, we are often interested in the transient response when no external voltage source is applied, i.e., $V_S(t) = 0$. In this case, the equation simplifies to the homogeneous equation:

$$ \frac{d^2i(t)}{dt^2} + \frac{1}{LC} i(t) = 0 $$

This is the equation for simple harmonic motion. The characteristic equation is:

$$ r^2 + \frac{1}{LC} = 0 $$

$$ r^2 = -\frac{1}{LC} $$

$$ r = \pm j \sqrt{\frac{1}{LC}} $$

Let $\omega_0 = \sqrt{\frac{1}{LC}}$, where $\omega_0$ is the natural angular frequency of the LC circuit. The general solution for the current in the homogeneous case is:

$$ i(t) = A \cos(\omega_0 t) + B \sin(\omega_0 t) $$

Where $A$ and $B$ are constants determined by the initial conditions.

### 4. General Solution with Voltage Source

If there is a voltage source $V_S(t)$, the complete solution is the sum of the homogeneous solution $i_h(t)$ and a particular solution $i_p(t)$:

$$ i(t) = i_h(t) + i_p(t) $$

The particular solution depends on the form of $V_S(t)$. For example, if the voltage source is a constant $V_0$ (DC voltage), the steady-state current $i_p(t)$ would be zero (since a DC source in series with an ideal inductor leads to zero steady-state current). The transient response would then be given by the homogeneous solution with constants determined by the initial charge on the capacitor and initial current through the inductor.

If the voltage source is sinusoidal, $V_S(t) = V_m \cos(\omega_s t + \phi_s)$, where $\omega_s$ is the source angular frequency, we can find a particular solution of the form $i_p(t) = I_m \cos(\omega_s t + \theta_i)$.

Using phasor analysis, the impedance of the inductor is $Z_L = j\omega_s L$ and the impedance of the capacitor is $Z_C = \frac{1}{j\omega_s C} = -\frac{j}{\omega_s C}$. The total impedance of the series circuit is:

$$ Z_{total} = Z_L + Z_C = j\omega_s L - \frac{j}{\omega_s C} = j\left(\omega_s L - \frac{1}{\omega_s C}\right) $$

For a DC voltage source ($V_S(t) = V_0$, so $\omega_s = 0$), the impedance of the capacitor approaches infinity, effectively blocking the DC current in the steady state. The inductor impedance approaches zero.

For an AC voltage source, the current amplitude is given by Ohm's law in phasor form:

$$ I_m = \frac{V_m}{|Z_{total}|} = \frac{V_m}{\left|\omega_s L - \frac{1}{\omega_s C}\right|} $$

The phase angle of the current relative to the voltage is:

$$ \theta_i = -\arg(Z_{total}) = -\left(\frac{\pi}{2} - \arctan\left(\omega_s^2 LC\right)\right) = \arctan\left(\frac{1}{\omega_s L - \frac{1}{\omega_s C}}\right) $$

### 5. Key Formulas Summary

For a series LC circuit:

1.  **Differential Equation:**
    $$ \frac{d^2i(t)}{dt^2} + \frac{1}{LC} i(t) = \frac{1}{L} \frac{dV_S(t)}{dt} $$

2.  **Natural Angular Frequency:**
    $$ \omega_0 = \sqrt{\frac{1}{LC}} $$

3.  **Current in Homogeneous Case (Free Oscillation):**
    $$ i(t) = A \cos(\omega_0 t) + B \sin(\omega_0 t) $$

4.  **Impedance of Inductor:**
    $$ Z_L = j\omega L $$

5.  **Impedance of Capacitor:**
    $$ Z_C = -\frac{j}{\omega C} $$

6.  **Total Impedance:**
    $$ Z_{total} = j\left(\omega L - \frac{1}{\omega C}\right) $$

These formulas are fundamental for analyzing the behavior of LC circuits, including their use as resonant circuits in Tesla coils.
