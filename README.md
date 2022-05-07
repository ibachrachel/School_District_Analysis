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

> `tenth_graders_ths = school_data_complete_df.loc[(student_data_df["school_name"] == "Thomas High School") 
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

*Math and reading scores by grade*

The original results for Thomas High School yielded an average math score of 83.4% and an average reading score of 83.9%. After the ninth graders' data was removed from the analysis, the new table only displays the average scores in math and reading for tenth through twelfth graders. 

[Average Math Scores by Grade](https://user-images.githubusercontent.com/102566199/167240674-b103191e-90b2-4fff-b97b-58e01319d951.png)


*Scores by school spending*

Thomas High School's school spending won't change, even after the data was adjusted for the academic dishonesty. It will remain in the same range of $630-644 per student. 

[Thomas High's Spending Range](https://user-images.githubusercontent.com/102566199/167240863-49475893-69d2-4e48-9f86-880f0db46d65.png)

*Scores by school size*

Thomas High has around 1600 students, which places them in the medium school size bin. No noticable changes were able to be seen in the resulting table. Based on our formatting choice, we can't see the minute changes that must've occured in the decimals. 

[School size and Scores](https://user-images.githubusercontent.com/102566199/167240996-feb56a46-3edd-45dc-b012-1de4ca3bd88f.png)


*Scores by school type*

The removal of the ninth grader data did not affect the school type vs. scores table. The numbers all remained the same. From the data, we still can deduce that the charter schools have a higher overall passing rate as well as math and reading scores. 

[Scores by School Type after Adjusting](https://user-images.githubusercontent.com/102566199/167241108-33db16e7-621b-42b0-9d00-dd2ca7d61849.png)

## Summary 

*4 changes after the ninth graders data was removed.*

By adjusting the data and removing data that might have been tainted by academic dishonesty, we aired on the side of caution and made sure that any issues were taken care of. Thankfully, there were not any tremendous changes that resulted from the removal of the ninth graders data. There were a few changes though: the district summary was affected by the removal of the data and showed a drop in the overall passing percentages, the math and reading scores showed a small drop in passing percentages, the other grades within Thomas High were not affected by the academic dishonesty of the ninth graders, and there were minute decrease in the passing percentage when compared with the school size, type, and spending. 
