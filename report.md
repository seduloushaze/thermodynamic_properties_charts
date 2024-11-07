# Thermodynamic Property Chart Generation for a Single-Component Material

## Objective
Generate a comprehensive set of thermodynamic property charts for a chosen single-component material, using accessible data for ideal gas specific heat and a suitable volumetric equation of state (EoS). The following key thermodynamic properties should be analyzed and visualized:
- Pressure-Volume (P-V) Diagram
- Pressure-Enthalpy (P-H) Diagram
- Temperature-Entropy (T-S) Diagram
- Other relevant property plots as necessary

## Material Selection
Select a material with:
- Available data for **ideal gas specific heat** values (e.g., \( C_p \), \( C_v \))
- **Equation of State** (EoS) data to account for real gas behavior (e.g., van der Waals, Redlich-Kwong, Peng-Robinson EoS)


## Methodology

### Step 1: Gather Data
1. **Ideal Gas Properties**: Obtain specific heat values \( C_p \) and \( C_v \) as functions of temperature, ideally in a tabulated or empirical form.
2. **Volumetric Equation of State**: Choose a suitable EoS for the material to model P-V-T behavior, options:
    - **Ideal Gas Law** (for ideal behavior approximations)
    - **van der Waals EoS**
    - **Peng-Robinson EoS**
    - **Redlich-Kwong EoS**

### Step 2: Code-Based Calculation
Develop a Python script to calculate thermodynamic properties:
- **Pressure (P)**, **Volume (V)**, **Enthalpy (H)**, **Entropy (S)**, and **Temperature (T)** based on the selected material's properties and EoS.
- Use fundamental thermodynamic relationships and properties from the EoS to derive values.

### Step 3: Define Property Relationships
1. **P-V Relationship**: Use the EoS to model isotherms across a range of volumes and pressures.
2. **P-H Relationship**: Integrate enthalpy values at different states, leveraging the specific heat data and EoS.
3. **T-S Relationship**: Calculate entropy changes for isothermal or isobaric conditions using specific heat data.

### Step 4: Visualize Thermodynamic Properties
Plot each property using Python's `Plotly` or a similar library. Suggested visualizations:
- **P-V Diagram**: Plot isotherms on a P-V graph.
- **P-H Diagram**: Plot isotherms on a P-H graph.
- **T-S Diagram**: Plot isobars  on a T-S graph.
- **P-S Diagram**: Plot isotherms on a P-S graph.


### Step 5: Validation and Comparison
Compare the calculated outputs with experimental data when available to ensure model accuracy.

# Thermodynamic Properties Analysis of Formaldehyde

## Compound Selection: Formaldehyde

Formaldehyde was selected for this analysis due to its significant industrial and medical applications. Formaldehyde and its derivatives play a crucial role in the upstream supply chain, aiding in the production of compounds essential for life-saving medical devices, such as:
- **Pacemakers**
- **Artificial heart valves**
- **Prostheses**

In addition to its use in manufacturing medical devices, formaldehyde is well known as a preservative in medical laboratories and is commonly used as a sterilizing agent. Key applications in the pharmaceutical and medical industries include:

- **Anti-infective drugs**: Formaldehyde serves as an active ingredient, promoting maximum absorption in gel capsules.
- **Vaccine Production**: Formaldehyde is used to inactivate viruses and detoxify bacterial toxins in vaccines, including those for:
  - Influenza
  - Polio
  - Cholera
  - Hepatitis A
  - Diphtheria
  - Tetanus

- **Medical Research**: Formaldehyde is widely used in pharmaceutical research, especially in the fields of **proteomics** and **genomics**.

![Image Placeholder](./Picture1.png)


## Data Source

The thermodynamic properties data for formaldehyde used in this analysis is derived from the following source:

> Koo, Raymond H. (1961). *Thermodynamic Properties of Formaldehyde*. Master's Thesis, Newark College of Engineering, New Jersey Institute of Technology. Available at: [Digital Commons @ NJIT](https://digitalcommons.njit.edu/cgi/viewcontent.cgi?article=2539&context=theses)

This source provides essential information on formaldehyde's thermodynamic properties, including specific heats, enthalpy, entropy, and equations of state, which are foundational for generating accurate property charts.


# Constants in SI Units

- **Trs**: Reference temperature = 298.15 K
## Specific Heat Capacity `C_p` Constants

The following constants are used to calculate the specific heat capacity at constant pressure ` C_p ` for formaldehyde:

- **\( a_1 \)**: 39.6463 J/mol
- **\( b_1 \)**: 0.03825 J/(mol·K)
- **\( c_1 \)**: -2.6776 × 10⁻⁶ J/(mol·K²)

The \( C_p \) value for formaldehyde can be expressed as a temperature-dependent equation:

$$
C_p(T) = a_1 + b_1 \cdot T + c_1 \cdot T^2
$$


where:
- **\( T \)** is the temperature in Kelvin (K)
- **\( C_p(T) \)** is the specific heat capacity in J/(mol·K)

This equation provides the temperature-dependent \( C_p \) values, which are essential for calculating enthalpy and entropy changes across different thermodynamic states.


- **R**: Ideal gas constant = 8.314 J/(mol·K)
- **Tc**: Critical temperature = 414.48 K
- **Pc**: Critical pressure = 6.8 × 10⁶ Pa
- **ω**: Acentric factor (dimensionless) = 0.215

## Peng-Robinson Equation Parameters

The Peng-Robinson equation of state is used to model the thermodynamic behavior of formaldehyde. The parameters for the equation are calculated as follows:
- **a**: Attraction parameter  
  $$ a = 0.45724 \times \frac{R^2 \times Tc^2}{Pc} $$
  Resulting units: Pa·m⁶ / mol²

- **b**: Repulsion parameter  
  $$ b = 0.07780 \times \frac{R \times Tc}{Pc} $$
  Resulting units: m³ / mol


These parameters are essential for calculating properties such as pressure and volume under various temperature conditions, providing a more accurate model for real gas behavior.

# Peng-Robinson Equation of State

To calculate the **Peng-Robinson equation of state** with temperature dependence, the following parameters and equations are used:

### 1. Temperature-Dependent Parameter \( \alpha \):

$$
k = 0.37464 + 1.54226 \cdot \omega - 0.26992 \cdot \omega^2
$$

$$
\alpha = \left( 1 + k \cdot \left( 1 - \sqrt{\frac{T}{T_c}} \right) \right)^2
$$

### 2. Peng-Robinson Equation of State:

$$
P = \frac{R \cdot T}{V_m - b} - \frac{a \cdot \alpha}{V_m^2 + 2 \cdot b \cdot V_m - b^2}
$$

where:
- \( T \) is the temperature,
- \( T_c \) is the critical temperature,
- \( \omega \) is the acentric factor,
- \( R \) is the ideal gas constant,
- \( a \) and \( b \) are Peng-Robinson constants, and
- \( V_m \) is the molar volume.

# Libraries Used in the Project

## 1. **NumPy**
   - **Installation**: `%pip install numpy`
   - **Description**: NumPy is a fundamental library for numerical computations in Python, providing support for multi-dimensional arrays and mathematical functions.
   - **Usage in This Project**:
      - **Array Operations**: NumPy is used to manage arrays and vectors, which store values like temperature, pressure, and volume at different stages of calculations. This improves the efficiency of the data processing and ensures that the operations are fast and memory-efficient.
      - **Mathematical Functions**: Functions like `np.sqrt()`, `np.log()`, and `np.real()` are used to perform essential mathematical operations required in the Peng-Robinson equation of state, optimization, and the calculation of compressibility factors and enthalpy.

## 2. **SciPy**
   - **Installation**: `%pip install scipy`
   - **Description**: SciPy is an open-source library built on top of NumPy, extending its functionality for advanced scientific and technical computing. It contains modules for optimization, integration, interpolation, and other mathematical operations.
   - **Usage in This Project**:
      - **Optimization**: The `scipy.optimize.minimize_scalar` function is used to perform optimization tasks on the volume (`Vm`) in the Peng-Robinson equation to find the minimum and maximum pressures for a given temperature. This is essential for calculating the pressure and volume relationship and determining the saturation pressure at different temperatures.

## 3. **Plotly**
   - **Installation**: `%pip install plotly`
   - **Description**: Plotly is a graphing library used for interactive data visualization in Python, allowing for the creation of customizable and visually appealing plots.
   - **Usage in This Project**:
      - **Interactive Plotting**: Plotly is used to plot the enthalpy (`H`) vs pressure (`P`) curves at different temperatures. The `go.Figure()` and `go.Scatter()` functions help in creating interactive line plots, making it easier to analyze and visualize the relationships between the properties of formaldehyde (e.g., pressure, volume, and enthalpy) at different temperatures.
      - **Visualization**: The plots provide insight into the behavior of the system, showing the changes in enthalpy as the pressure varies for each temperature, and allowing users to interact with the plot for better understanding.





