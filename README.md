# 📊 AB Testing Methodology

## What is an A/B Test?

A/B testing is a controlled experiment used to compare two versions (A and B) of a feature, product, or experience to determine which one performs better with respect to a defined objective.

In A/B testing:  
- **Group A** is typically the control (existing version)  
- **Group B** is the variant (new version with changes)  

It helps answer:  
**"Does the new version create a statistically significant improvement over the existing one?"**



## 🧪 A/B Testing Process

### 1. Identify Your Business Problem

Define the user journey and the desired change.  
**Example**: We want to test if a digital flyer on the homepage increases online conversion.



### 2. Identify Your Target KPI

Choose metrics aligned with your goals (e.g., Sales, Web Visits, Add to Cart, TOF, BOF, Order, conversion rate, click-through rate, etc.).  
Clearly define **success criteria** before starting.



### 3. Pre-Analysis Setup

#### Explore the Data  
Perform exploratory data analysis (EDA).  
Check the distribution of your key metrics:  
- Is it normally distributed?  **Shipiro Wilk** test to check for normality
- Any outliers?

#### State Your Hypotheses  
- **Null Hypothesis (H₀)**: There is no difference between Group A and Group B.  
- **Alternative Hypothesis (H₁)**: There is a difference between Group A and Group B.

#### Set Experimental Parameters  
- **Significance Level (α)**: Typically set to `0.05`.  
- **Statistical Power (1 - β)**: Usually `0.80`  
- **Minimum Detectable Effect (MDE)**: Smallest effect size you consider meaningful  
  - _Example_:  
    - 5% Lift → 15 days needed  
    - 10% Lift → 25 days needed



### 4. Design Your Experiment

- **Split Test Groups**: Divide users into control and test groups  
- **Randomization**: Ensure unbiased assignment  
- **Bootstrap Sampling** _(optional)_: For robust simulation  
- **Effect Size**: Estimate the detectable difference  
- **Sample Size Calculation**: Use power analysis  
- **Test Duration**: Based on traffic and MDE  

**Conclusion from Pre-Analysis**:  
A minimum 5% change is necessary for statistically significant results within 15 days.



### 5. Check for Validity Threats

**Run an A/A Test**:  
Split users into two identical groups with no changes  
- **Purpose**: Validate randomization and system consistency



## 📊 Statistical Testing

### Validate Assumptions  
- **Normality Test**: Use Shapiro-Wilk (for small samples)

### Choose Statistical Test  
- If **normal**: Use **t-test**  for two groups  or **Anova test** for multiple groups
- If **non-normal**: Use **Mann-Whitney U test** or **Kruskal Wallis test** for multiple groups
#### For Binary & Categorical outcomes 
- If **normal**: Use **Chi square test** (compare category choices)  or **Proportion Z test** (compare proportions)
- If **non-normal**: Use **Fisher's Exact Test** (compare category choices) or **Barnards test** 



## 📈 Post-Analysis

- Compute **p-values** and **confidence intervals**  
- Evaluate **effect size** and **direction of change**  
- Interpret **practical** and **statistical significance**

**Draw Conclusions**  
- Was the change statistically significant?  
- Was it practically valuable?  
- Should you roll out, iterate, or discard?

**Example Conclusion**:  
> “There is no statistically significant difference between the test and control groups. Therefore, the new feature does not impact sales and should not be implemented.”  
Also evaluate practical value: e.g., **ROAS**, **ROI**



## 🛠️ Tools You Can Use

- **Statistical Tests**: `scipy.stats`, `statsmodels`  
- **EDA & Visualization**: `pandas`, `matplotlib`, `seaborn`  
- **Sample Size & Power**: `statsmodels.stats.power`


<br><br><br><br>

# A/B Testing for Urban Wear 🚀
This repository contains a sample A/B test design for an e-commerce platform called Urban Wear.

### Business Problem
Urban Wear, a clothing brand, is preparing to launch its new e-commerce store. Currently, the pre-launch page is focused on collecting email sign-ups from site visitors. The goal is to maximize the number of email sign-ups for the website launch.

### A/B Test Objective
As a product data scientist at Urban Wear, the goal is to design, execute, and analyze an A/B test that evaluates two versions of the email sign-up button on the pre-launch page:
Control: Blue submit button (current version)
Treatment: Green submit button
The objective is to determine whether the green button improves email sign-up rates compared to the blue button.

### Steps for A/B Testing
Load and Explore the Dataset


### Conduct exploratory analysis to understand traffic, sign-up rates, and distribution.
State the Hypothesis
1. **Null Hypothesis (H₀)**: The green submit button does not improve the email sign-up rate compared to the blue button.
2. **Alternative Hypothesis (H₁)**: The green submit button improves the email sign-up rate compared to the blue button.

### Design the Experiment
1.**Calculate Sample Size**: Determine the minimum number of visitors needed for each group to detect a meaningful difference with statistical power (e.g., 80%).
2.**Traffic Allocation**: Split site visitors into equal groups (e.g., 50% Control, 50% Treatment).
3.**Daily Traffic Estimation**: Estimate the daily number of visitors available for the test.
4.**Experiment Duration**: Calculate how long the test should run to collect sufficient data.

### Run the A/B Experiment
Randomly assign visitors to either the control group (blue button) or the treatment group (green button).
Collect data on email sign-up rates for both groups.
Analyze the Results

### Assess Validity Threats
Ensure the integrity of the experiment by performing validity checks:
1. **AA Test**: Conduct an AA test to confirm there is no inherent difference between the control and treatment groups before starting the A/B test.
2. **Chi-Square Test for Sample Ratio Mismatch (SRM)**: Run a chi-square test to check if randomization led to balanced sample sizes between groups.
3. **Additional checks like Segmentation Analysis or Novelty Checks** may be performed to identify any biases or confounding factors.

### Conduct Statistical Inference
Apply statistical tests to evaluate the results:
1. **Chi-Squared Test**: Compare proportions between the control and treatment groups (e.g., email sign-up rates).
2. **T-Test**: Compare the means of the two groups to determine if the difference is statistically significant.
3. **Confidence Interval (CI)**: Calculate a 95% confidence interval to determine the range within which the true effect lies.

### How to Use This Repository
Clone the Repository
bash
Copy code
git clone 
cd ab-testing-urbanwear
Install Dependencies
Ensure you have Python installed, then install the required libraries:
bash
Copy code
pip install -r requirements.txt

### Run the Analysis
Open the notebook ab_test_analysis.ipynb in Jupyter Notebook or any compatible IDE to follow the A/B test process step-by-step.

### Contributing
Contributions are welcome! To contribute:

### Fork the repository.
Create a new branch (git checkout -b feature-name).
Commit your changes (git commit -m "Add feature").
Push to the branch (git push origin feature-name).
Open a Pull Request.

### License
This project is licensed under the MIT License.
