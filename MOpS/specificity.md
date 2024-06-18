system_msg = "You are an expert in evaluating comprehensive product opinion summaries created using multiple attributes from the input. The input includes product title, description, key features, specifications, reviews, and average rating. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each product individually, ranging from 1 to 5, to a summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"


specificity_prompt_template = '''
Task Description:

{system_message}

You will be given comprehensive information about a product, including product title, description, key features, specifications, reviews, and average rating, using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the product opinion summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided comprehensive product information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the product opinion summary follows the metric.

Generic Opinion Example: "The battery is good."

Specific Opinion Example: "The battery lasts for more than 12 hours on a single charge."

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all while generating the summary from  the input, including product title, description, key features, specifications, reviews, and average rating, and all the information and opinions presented in the summary are generic.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from  the input, including product title, description, key features, specifications, reviews, and average rating, and most of the information and opinions presented are generic.

<score>3</score> - The metric is followed reasonably while generating the summary from  the input, including product title, description, key features, specifications, reviews, and average rating, and only around half of the information and the opinions presented are specific.

<score>4</score> - The metric is followed mostly while generating the summary from  the input, including product title, description, key features, specifications, reviews, and average rating, and most of the information and opinions presented in the summary are specific. 
Very few information and opinions are generic.

<score>5</score> - The metric is followed thoroughly while generating the summary from  the input, including product title, description, key features, specifications, reviews, and average rating, and all the information and opinions presented in the summary are specific 

Metric:

Specificity: The summary should avoid containing generic information and opinions. All information and opinions within the summary should be detailed and specific about the product and the consensus of views. Summaries should be penalized for missing details and rewarded if they are specific and cover the details.

Product Information:

Product Title: {product_title}

Description: {description}

Key Features: {key_features}

Specifications: {specifications}

Reviews: {reviews}

Average Rating: {average_rating}

Summary: {Product_Opinion_Summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the summary according to the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through the summary and list all the opinions presented.
3. Check if details are presented for the opinions. Classify each opinion as specific or generic.
4. Count the number of generic and specific occurrences.
5. Give a step-by-step explanation if the summary adheres to the metric considering the product title, description, key features, specifications, reviews, and average rating as the input. Stick to the metric only for evaluation.
6. Rate and Score: Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.
Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''