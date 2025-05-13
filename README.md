# Project Title: Heart Disease Analysis using Power BI
## Author: Anpothle Rohan
## Domain: Healthcare Analytics
## Tools Used: Power BI



# Project Overview
Heart disease is one of the leading causes of death globally. This project aims to analyze heart disease prevalence using an interactive Power BI dashboard. By leveraging demographic, health condition, and lifestyle factors, the dashboard helps identify key contributors and high-risk segments.

# Objective
To analyze the impact of various health conditions, behaviors, and demographics on heart disease prevalence.

To build an intuitive Power BI dashboard that provides actionable insights for healthcare professionals, analysts, and policymakers.

To highlight trends that can support preventive care strategies.

# Data Source:




# Data Fields Used:

• HeartDisease: Whether the individual have heart disease or not. (Target variable)

• BMI: Body Mass Index of the individual.

• Smoking: Whether the individual smokes or not.

• AlcoholDrinking: Whether the individual consumes alcohol or not.

• Stroke: History of stroke (Yes/No).

• PhysicalHealth: Physical health score.

• MentalHealth: Mental health score.

• Sex: Gender of the individual.

• AgeCategory: Age category of the individual.

• Race: Ethnicity or race of the individual.

• Diabetic: Diabetes status (Yes/No).

• PhysicalActivity: physical activity(Yes/No).

• GenHealth: General health rating.

• SleepTime: Average sleep time.

• Asthma: Asthma status (Yes/No).

• KidneyDisease: Presence or absence of kidney disease.

• SkinCancer: Presence or absence of skin cancer.

# Preprocessing:

1. Null values removed

2. Categorical values encoded for clarity

3. Calculated additional columns for rate-based KPIs using DAX

4. Created categorized versions of continuous variables for better segmentation (e.g., PhysicalHealth_Category)


# Dashboard Features
1. **KPI Tiles**

      Heart_Disease_Rate: **8.56%**
   
      HD_Rate_By_Diabetes: **21.95%**
      
      HD_Rate_By_KidneyDisease: **29.33%**
      
      HD_Rate_By_Stroke: **36.37%**
      
      Average_BMI_HeartDisease: 29.4

2. **Charts & Visuals**

      **Heart Disease Rate by Age Category**: Shows a steep increase with age
      
      **Heart Disease Rate by Physical Health Category**: Worse physical health is linked with higher heart disease

      **Heart Disease Rate by Mental Health Category**: Worse Mental health is linked with higher heart disease
      
      **Heart Disease by Lifestyle**: Alcohol drinking, smoking habits vs heart disease prevalence
      
      **Heart Disease Rate by General Health**: Poor-rated individuals show a very high heart disease rate (34%)
      
      **Race-wise Distribution**: Visual comparison of heart disease rates across racial categories

3. **Interactive Features**

      Clear all slicers button
      
      Gender filter buttons
      
      Responsive KPIs and charts based on selection

# **DAX Measures (Sample)**

  1.
        **Heart_Disease_Rate** = 
          VAR Total_pop = COUNTROWS(Heart_disease)
          VAR Heart_diseased_pop = CALCULATE(COUNTROWS(Heart_disease), Heart_disease[HeartDisease] = "Yes")
          RETURN
          IF(
              Total_pop > 0,
              DIVIDE(Heart_diseased_pop, Total_pop) * 100,
              BLANK()
          )

   2.
        **HD_Rate_By_Diabet** = 
            VAR TotalDiabetic = CALCULATE(COUNTROWS(Heart_disease),ALLSELECTED(Heart_disease),Heart_disease[Diabetic]="Yes")
            VAR DiabeticHeartDisease = CALCULATE(COUNTROWS(Heart_disease),ALLSELECTED(Heart_disease),Heart_disease[Diabetic]="Yes",Heart_disease[HeartDisease]="Yes")
            RETURN
            IF(
                TotalDiabetic > 0,
                DIVIDE(DiabeticHeartDisease,TotalDiabetic)*100,
                BLANK()
            )

# **Key Findings**

  Age Dependency: Heart disease risk increases significantly after 60.
    
  General Health Correlation: People with "Poor" health rating have a 34% heart disease rate.
    
  Lifestyle Habits: Smoking and physical inactivity show a clear increase in heart disease cases.
    
  Comorbidities: Stroke and kidney disease are the most significant contributors.


# **Conclusion**
The Power BI dashboard delivers a powerful visualization tool to analyze and understand heart disease data. With easily digestible insights and interactive features, it supports data-driven decisions in healthcare and public health policy.



