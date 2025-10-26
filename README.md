# European Option Pricing on Bitcoin using Monte Carlo Simulation

This project implements a **risk-neutral Monte Carlo simulation** to price a **European call option on Bitcoin**. It also estimates the **implied volatility** using the **Newton–Raphson method**, initialized with the **Brenner & Subrahmanyam ATM approximation**.

This pricing framework is built to mimic real-world BTC option markets (such as Deribit) and supports visualizing simulated asset paths and terminal price distributions.

---

## Key Features

✔ Monte Carlo simulation under the Black–Scholes risk-neutral framework  
✔ Implied volatility calculation using Newton–Raphson refinement  
✔ Histogram of terminal asset prices with market price overlay  
✔ Time-path visualization of simulated Bitcoin price trajectories  
✔ Standard error estimation for pricing accuracy  
✔ Ready for extension to greeks, puts, or API-fed live option data  

---

## Financial Parameters (Notation)
| Symbol | Description                   | Units   |
|--------|------------------------------|---------|
| **S**  | Spot price of Bitcoin        | USD     |
| **K**  | Strike price of option       | USD     |
| **r**  | Risk-free interest rate      | Annual  |
| **T**  | Time to maturity (years)     | Years   |
| **N**  | Number of time steps         | Integer |
| **M**  | Number of simulated paths    | Integer |
| **C_mkt** | Observed market option price | USD |
| **σ**  | Implied volatility (computed) | Annualized |

---

## Model Overview

### Price Dynamics (Geometric Brownian Motion)
\[
dS_t = rS_t dt + \sigma S_t dW_t
\]
\[
S_{t+\Delta t} = S_t \cdot \exp\left( \left(r - \frac{1}{2}\sigma^2\right)\Delta t + \sigma \sqrt{\Delta t} Z \right)
\]

### Monte Carlo Option Pricing
\[
C_0 = e^{-rT} \cdot \mathbb{E}[\max(S_T - K, 0)]
\]

### Implied Volatility Estimation
- Initial guess via Brenner & Subrahmanyam:
  \[
  \sigma \approx \sqrt{2\pi} \cdot \frac{C_mkt}{S \sqrt{T}}
  \]
- Refined using Newton–Raphson until convergence.

---

## Visual Outputs Included
- Simulated BTC price paths  
- Histogram of final BTC prices vs market option price  
- Mean price path visualization  
- Standard error of the simulation  

---

## How to Run

### Install dependencies:
```bash
pip install -r requirements.txt
