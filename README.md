# Detailed Comments and Theory on the Vibration Analysis Codes

## Theory Behind the Code

This collection of codes focuses on analyzing three distinct types of vibration scenarios: undamped free vibration, undamped forced vibration, and viscous damped free vibration. Each code explores the mathematical models governing these phenomena and provides numerical solutions along with graphical representations.

---

### 1. Undamped Free Vibration

**Physical Model**:
- A mass-spring system oscillates without any energy dissipation.
- Governed by the equation:
  m (d^2x/dt^2) + kx = 0
  where m is the mass, k is the spring stiffness, and x is the displacement.

**Key Concepts**:
- **Natural Frequency**: omega_n = sqrt(k / m)
- **Solution**: The general solution is given by:
  x(t) = C1 cos(omega_n t) + C2 sin(omega_n t)
  Constants C1 and C2 are determined by initial conditions.

**Equations**:
- Displacement: x(t) = C1 cos(omega_n t) + C2 sin(omega_n t)
- Velocity: v(t) = -C1 omega_n sin(omega_n t) + C2 omega_n cos(omega_n t)
- Acceleration: a(t) = -C1 omega_n^2 cos(omega_n t) - C2 omega_n^2 sin(omega_n t)

**Code Features**:
- Calculates displacement, velocity, and acceleration as functions of time.
- Plots the position, velocity, and acceleration profiles over time.

**Example Input**:
- Mass: 10 kg
- Stiffness: 200 N/m
- Initial displacement: 0.1 m
- Initial velocity: 0 m/s
- Duration: 10 s
- Number of points: 1000

**Example Output**:
- Natural Frequency: 4.47 rad/s
- Plots for position, velocity, and acceleration.

---

### 2. Undamped Forced Vibration

**Physical Model**:
- A mass-spring system subjected to an external periodic force:
  m (d^2x/dt^2) + kx = F(t)

**Key Concepts**:
- **Natural Frequency**: omega_n = sqrt(k / m)
- **Forcing Function**: Periodic force, e.g., F(t) = F0 sin(omega t).
- **Resonance**: Occurs when forcing frequency omega matches natural frequency omega_n.

**Equations**:
- General solution for steady-state response:
  x(t) = F0 / (k - m omega^2) sin(omega t)
  where omega is the forcing frequency.
- Resonance (omega = omega_n) results in unbounded displacement:
  x(t) = X * t * sin(omega t)
  where X = F0 / (2 m omega_n).

**Code Features**:
- Handles arbitrary forcing functions provided by the user.
- Detects and visualizes resonance scenarios.
- Plots displacement, velocity, and acceleration profiles.

**Example Input**:
- Mass: 5 kg
- Stiffness: 500 N/m
- Force: 10 sin(5t)
- Forcing Frequency: 5 rad/s
- Duration: 10 s
- Number of points: 1000

**Example Output**:
- Natural Frequency: 10 rad/s
- Plots for position, velocity, and acceleration.
- Indicates resonance if applicable.

---

### 3. Viscous Damped Free Vibration

**Physical Model**:
- A mass-spring system with energy dissipation:
  m (d^2x/dt^2) + c (dx/dt) + kx = 0
  where c is the damping coefficient.

**Key Concepts**:
- **Damping Ratio**: zeta = c / (2 sqrt(km))
- **Types of Damping**:
  - **Underdamped**: zeta < 1
    - Displacement: x(t) = D e^(-zeta omega_n t) sin(omega_d t + phi)
    - omega_d = omega_n sqrt(1 - zeta^2)
  - **Critically Damped**: zeta = 1
    - Displacement: x(t) = (A + Bt)e^(-omega_n t)
  - **Overdamped**: zeta > 1
    - Displacement: x(t) = A e^(lambda1 t) + B e^(lambda2 t)
    - lambda1 and lambda2 are roots of the characteristic equation.

**Equations**:
- Underdamped:
  - x(t) = D e^(-zeta omega_n t) sin(omega_d t + phi)
  - omega_d = omega_n sqrt(1 - zeta^2)
- Critically Damped:
  - x(t) = (A + Bt)e^(-omega_n t)
- Overdamped:
  - x(t) = A e^(lambda1 t) + B e^(lambda2 t)

**Code Features**:
- Handles all damping scenarios.
- Plots displacement, velocity, and acceleration profiles.

**Example Input**:
- Mass: 2 kg
- Stiffness: 300 N/m
- Damping Coefficient: 10 Ns/m
- Initial displacement: 0.05 m
- Initial velocity: 0.1 m/s
- Duration: 5 s
- Number of points: 500

**Example Output**:
- Natural Frequency: 12.25 rad/s
- Critical Damping Coefficient: 24.5 Ns/m
- Plots for position, velocity, and acceleration.
- Indicates damping type (e.g., underdamped).

---

## Differences Among the Codes

1. **Undamped Free Vibration**:
   - No external forces or energy dissipation.
   - Pure sinusoidal motion governed by the natural frequency.

2. **Undamped Forced Vibration**:
   - External force drives the system.
   - Resonance occurs when forcing frequency matches natural frequency.

3. **Viscous Damped Free Vibration**:
   - Includes energy dissipation.
   - Motion depends on the damping ratio (underdamped, critically damped, overdamped).

---

## Visualization and Insights
- Each code provides intuitive plots for position, velocity, and acceleration.
- These plots help understand the dynamics and effects of forces, damping, and resonance in mechanical systems.
- The codes are modular, allowing easy adaptation to various scenarios.
