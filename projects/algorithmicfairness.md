# AI for Fair Hiring: A Holistic Approach to Recruitment and Group Fairness

- [Project Report](https://github.com/user-attachments/files/18854624/CS_256__Project_Template__Copy_.pdf)

## Overview

In this project, we developed an AI-driven framework aimed at improving the fairness of the hiring process. The primary goal was to create a system that not only ensures fairness in terms of group quotas but also takes into account the performance potential of candidates, making sure that the hiring algorithm maximizes the success of selected candidates. We address both group fairness and individual fairness, with a specific focus on preventing discrimination based on protected attributes such as political affiliation, pregnancy status, gender, race, and more.

The system includes a transcription algorithm and a distance metric that ensures fairness, transparency, and accuracy in recruitment decisions. The project also draws from research and studies in the domain of AI fairness, particularly those related to college admissions and other decision-making processes that involve sensitive and protected attributes.

## Project Goals

1. **Fairness in Hiring**: We aimed to ensure that candidates from different groups (e.g., gender, race) were treated fairly, with the number of applicants hired from each group proportional to the quotas set by the hiring institution.
   
2. **Success Maximization**: The hiring algorithm not only ensured group fairness but also maximized the chances of success for the candidates hired, avoiding situations where candidates who were unlikely to succeed were selected just to meet quotas.
   
3. **Distance Metric for Fairness**: A custom distance metric, designed to be blind to protected attributes, was introduced to measure the similarity between candidates. This distance metric was crucial for ensuring that group fairness was enforced while maintaining a focus on the competence and performance potential of each candidate.
   
4. **AI and Group Fairness**: We ensured that the transcription algorithm used to process applicants’ data was free from discrimination based on protected attributes. We used a distance metric to enforce group fairness and prevent AI-based discrimination, ensuring that no protected attributes impacted the selection process.

## Key Features

### 1. **Quotas and Group Fairness**

Our model makes the assumption that the hiring institution has already determined the quotas for each group. The AI framework ensures that the total number of applicants hired is equal to the total number of job openings, and that the number of applicants hired from each group is proportional to their designated quota. The key formulas used to enforce group fairness are:

\[
E[\sum_{j=1}^{m} \mathbf{1}[D(j, T_j) = \emptyset]] = Q
\]
\[
E[\sum_{j=1}^{m} \mathbf{1}[D(j, T_j) = j]] = Q_{j}
\]

Where:
- \( D(j, T_j) \) represents the decision algorithm applied to group \( j \),
- \( Q \) represents the total number of job openings,
- \( Q_j \) represents the quota for group \( j \).

This ensures that each group is represented fairly according to its predetermined quota.

### 2. **Minimizing Bias in the Hiring Process**

A key issue in achieving fairness is ensuring that AI does not inadvertently hire candidates who are less likely to succeed simply to meet quotas. Therefore, our hiring algorithm maximizes the chances of hiring successful candidates by considering both the competence and suitability of applicants for the position. By utilizing a distance metric, the algorithm can assess the success likelihood of candidates based on their qualifications and attributes, ensuring that the most capable candidates are selected within each group.

### 3. **Protected Attributes and Discrimination Avoidance**

We also introduced the concept of protected attributes, which refer to attributes such as political affiliation, gender, pregnancy status, and other sensitive characteristics. Our transcription algorithm, which processes applicants’ data, was designed to be **attribute-blind**. This means that the algorithm does not make decisions based on protected attributes. To achieve this, we defined an **attribute-blind distance metric**:

\[
d(x_{\text{with attribute }a}, x_{\text{without attribute }a}) = 0
\]

This ensures that the distance metric, which is used to assess the similarity between applicants, does not take into account any protected attributes. As a result, the decision algorithm does not inadvertently discriminate based on these sensitive characteristics.

### 4. **Distance Metric and Individual Fairness**

To enforce fairness, we defined a custom distance metric \( d(x, y) \), which combines multiple similarity measures to calculate the "distance" between two applicants. This metric ensures that similar applicants receive similar treatment, a core tenet of **individual fairness**. The distance metric is designed to be blind to protected attributes, ensuring that it does not unfairly weigh applicants based on characteristics such as gender or race.

The final distance metric is a function of two different measures \( d_1(x, y) \) and \( d_2(x, y) \):

\[
d(x, y) = f(d_1(x, y), d_2(x, y))
\]

Where:
- \( d_1(x, y) \) measures the similarity between candidates based on qualifications and job-relevant features.
- \( d_2(x, y) \) measures similarity based on other general attributes, such as personal interests, excluding protected attributes.

The function \( f \) combines these two similarity measures to generate the final "distance" between two candidates, ensuring both fairness and competence.

### 5. **Fairness in Recruitment Processes Across Different Roles**

We recognize that different departments or roles within an institution may have different needs and criteria for hiring. For instance, the Department of Defense may have different skill set requirements compared to a Department of Speech Writing. Our approach adapts to these differences by implementing **individual fairness within departments**. This means that candidates applying for roles within the same department will be compared against each other based on their suitability for that particular role, rather than being compared to candidates in other departments.

## Challenges and Limitations

1. **Quantifying Similarity**: One of the main challenges faced in this project was the difficulty of quantifying the similarity between applicants in a meaningful way. Applicants come from diverse backgrounds, and their qualifications and experiences may not always be directly comparable. For example, two candidates with similar academic backgrounds but from different fields (e.g., technical vs. theoretical math) may not have a straightforward "distance" between them, complicating the fairness analysis.

2. **Impact of Different Departments**: While our individual fairness metric works well in a general hiring context, it may need to be adjusted for specific departments or roles with vastly different requirements. As discussed, departments may require different skills and have different thresholds for hiring, and this needs to be factored into the decision-making process to ensure fairness.

3. **Protected Attribute Transparency**: Despite our efforts to make the transcription algorithm attribute-blind, there is still the challenge of ensuring that no indirect biases emerge through other non-protected attributes. For example, if an applicant’s social network or writing style is inadvertently associated with certain demographics, the algorithm may still reflect bias.

## Related Work

This project builds on research in fairness and bias in AI, particularly in the context of recruitment and college admissions. The study by Alvero et al. (2023) highlighted the potential for AI systems to infer sensitive attributes such as gender and household income from applicants’ essays, emphasizing the need for fairness in AI-based decision-making. Additionally, research on AI fairness in college admissions has influenced our approach, as both processes involve holistic decision-making based on a wide range of public and protected information.

### Key References:
- Veldanda-Grob (2023). "AI and Protected Attributes in Hiring"
- U.S. Equal Employment Opportunity Commission (EEOC)
- Alvero et al. (2023), "Fairness in College Admissions and the Impact of AI"
  
## Future Directions

For future research, we propose the following areas of focus:
- **Incorporating Political Preferences**: We plan to explore how political preferences and other demographic information can be integrated into the model to create a more diversified and inclusive workforce.
- **Improved Similarity Metrics**: We aim to improve the similarity metric to better handle the complex nuances of applicants' qualifications, ensuring that it provides a more accurate and fair comparison.
- **Department-Specific Fairness**: We will investigate how to adapt our fairness approach to cater to the specific needs of different departments, ensuring that fairness is maintained even when hiring criteria vary significantly.

## Conclusion

The AI for Fair Hiring project developed a framework that ensures fairness in recruitment while maximizing the potential for candidate success. By using a custom-designed distance metric and focusing on both group fairness and individual fairness, the system helps mitigate bias and discrimination in the hiring process. This project contributes to ongoing efforts to create more equitable and transparent AI systems for critical decision-making processes.

