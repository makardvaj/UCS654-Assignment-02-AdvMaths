# Predictive Analysis: PDF Estimation for Air Quality Data

## Project Description
This project focuses on modeling the probability density of NO2 concentration levels from the India Air Quality dataset . The methodology involves a non-linear transformation of the input feature based on university roll number parameters, followed by the estimation of a Gaussian-style Probability Density Function (PDF) .

## Methodology

### Step 1: Data Transformation
The NO2 feature ($x$) is transformed into a new variable $z$ using a parameterized non-linear model :
$$z = T_{r}(x) = x + a_{r}\sin(b_{r}x)$$ 

The parameters $a_r$ and $b_r$ are derived from the University Roll Number ($r = 102316037$):
* $a_r = 0.05 \times (r \pmod 7)$ 
* $b_r = 0.3 \times ((r \pmod 5) + 1)$ 

For $r = 102316037$:
* $a_r = 0.05 \times 5 = 0.25$
* $b_r = 0.3 \times (2 + 1) = 0.9$

### Step 2: PDF Parameter Estimation
The transformed variable $z$ is modeled using the predicted probability function :
$$\hat{p}(z) = c \cdot e^{-\lambda(z-\mu)^{2}}$$ 

The parameters are estimated using the following statistical properties:
* **$\mu$ (mu)**: The sample mean of the transformed variable $z$.
* **$\lambda$ (lambda)**: Defined as $\frac{1}{2\sigma^2}$, where $\sigma$ is the standard deviation of $z$.
* **$c$**: The normalization constant $\sqrt{\frac{\lambda}{\pi}}$, ensuring the total area under the PDF curve equals 1.

---

## Results

### Parameter Values
Based on the implementation for Roll Number 102316037, the learned parameters are:

| Parameter | Value |
| :--- | :--- |
| **Mean ($\mu$)** | 25.8027 |
| **Lambda ($\lambda$)** | 0.00146 |
| **Constant ($c$)** | 0.02155 |

### Result Visualization
The graph below compares the actual distribution of the transformed data $z$ with the learned PDF model $\hat{p}(z)$.



---

## Conclusion
The model successfully approximates the distribution of the transformed NO2 data. The values of $\mu$, $\lambda$, and $c$ represent the central tendency, spread, and normalization of the transformed air quality feature respectively .
