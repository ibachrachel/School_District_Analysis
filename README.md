# School_District_Analysis

## Overview

*Purpose*

The Chief Data Scientist for a school district is analyzing informatino from many sources and formats. She's been tasked with prepping all the standardized test data for analysis. The reporting and presentation of the findings will provide insights about the performance trends and patterns. Based on these trends and patterns, the school board and superintendent will make decisions for the budget allotment. The current assignment is to analyze school data using specific metrics to focus on differing grade levels, school size, school type, and more. Since data isn't always perfect, the data will have to be under targeted review to pick out data that will affect the overall analysis. Once this cleaning of the data is complete, summaries of the data can be produced for the stakeholders' review. 

## Results

*Background* 

Once the analysis was complete, it was reviewed by the school board and the superintendent to better inform future decisions for the district. Unfortunately, the school board has notified the Chief Data Scientist and her department that the student data file revealed evidence of academic dishonestly. The ninth graders at a high school in the district have altered their math and reading scores. This data cannot be submitted to the state for review, so we must scrub the data of all the ninth grade student data and then reflect on how it changes patterns and performance trends. 


- How is the district summary affected?

After the ninth grader data had been replaced with NaN values for every math and reading score, we were able to compare the data with and without the influence of these values. As shown in the images below, there is not a huge difference between the passing percentages. Both the passing math percentage and the passing reading percentage only differed by 0.1%. The overall passing has a difference of 0.3%. There is not a huge effect when we remove the ninth graders data. This is actually a good thing. If we removed the data and it shifted a dramatic amount, we would know that the academic dishonesty had significantly affected the performance trends. 

[District Summary WITHOUT ninth graders](https://user-images.githubusercontent.com/102566199/167239620-d8df9b88-a1e7-4ca4-9089-bff82eef31f3.png)

[District Summary WITH ninth graders](https://user-images.githubusercontent.com/102566199/167239637-8126ccc4-f352-405e-8ce9-0929c9cd1460.png)


- How is the school summary affected?

The ninth grader data had a significant effect on the school summary. In this dataframe, the code analyzed each specific schoo site individually. To fully exclude the ninth graders data, the code had to be rewritten to only use the tenth through twelfth graders as students counted for the analysis.

`tenth_graders_ths = school_data_complete_df.loc[(student_data_df["school_name"] == "Thomas High School") 
                                                               & (student_data_df["grade"] == "10th")]

eleventh_graders_ths = school_data_complete_df.loc[(student_data_df["school_name"] == "Thomas High School") 
                                                               & (student_data_df["grade"] == "11th")]

twelfth_graders_ths = school_data_complete_df.loc[(student_data_df["school_name"] == "Thomas High School") 
                                                               & (student_data_df["grade"] == "12th")]

tenth_to_twelfth_ths_count = (len(tenth_graders_ths) + len(eleventh_graders_ths) + len(twelfth_graders_ths))`

This code allowed us to recalculate the passing math and reading percentages as well as the overall passing percentage. When comparing the school summaries produced before and after removing the ninth graders' data, there is a 25.8% difference in the overall passing rate. 

[School Summary BEFORE Adjusting for Academic Dishonesty](https://user-images.githubusercontent.com/102566199/167240155-5d363e6d-4760-4497-9fb7-9038b2b4c4a8.png)

[School Summary AFTER Adjusting for Academic Dishonesty](https://user-images.githubusercontent.com/102566199/167240184-4eb37149-288c-4ccd-a468-29753d480196.png)

After the ninth graders were removed, the overall passing percentages increased by a minimum of 20% across math, reading, and overall. This means that the academic dishonesty definitely affected the individual school summary and needed to be removed to accurately represent the performance of the Thomas High School. 

- How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

Similar to the overall difference in percentages seen in the district summary, Thomas High School's performance in relation with the other schools did not change. The original analysis resulted in Thomas High ranked second in the list of top performing schools, coming in at a 90.9% overall passing rate. The redone analysis kept Thomas High at number two, resulting in a overall passing percentage of 90.6%. 

[High Performing Schools After Adjustment](https://user-images.githubusercontent.com/102566199/167240404-a5f24238-dc44-4fca-b43e-a11f70785629.png)

- How does replacing the ninth-grade scores affect the following: 
- 
*Math and reading scores by grade*

*Scores by school spending*

*Scores by school size*

*Scores by school type*

## Summary 

Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs
