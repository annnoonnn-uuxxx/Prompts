system_msg = "You are an expert in evaluating comprehensive product opinion summaries created using multiple attributes from the input. The input includes product title, description, key features, specifications, reviews, and average rating. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each product individually, ranging from 1 to 5, to a summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"

relevance_prompt_template = '''
Task Description:

{system_message}

You will be given comprehensive information about a product, including product title, description, key features, specifications, reviews, and average rating, using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the product opinion summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided comprehensive product information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the product opinion summary follows the metric.

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary misses all the important opinions majorly discussed in the reviews and all the essential information from the the input, including product title, description, key features, specifications, reviews, and average rating.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary misses most of the important opinions majorly discussed in the reviews or mostly has redundant/excess/unimportant details from the input, including product title, description, key features, specifications, reviews, and average rating.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary covers around half of the important opinions majorly discussed in the reviews or contains redundant/excess/unimportant details from the input, including product title, description, key features, specifications, reviews, and average rating.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary covers most of the important opinions majorly discussed in the reviews and has significantly less amount of redundant/excess/unimportant details from the input, including product title, description, key features, specifications, reviews, and average rating.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information and covers all the important opinions majorly discussed in the reviews and has no redundant/excess/unimportant details from the input, including product title, description, key features, specifications, reviews, and average rating.




Metric:

Relevance: Selection of important information from the input, including product title, description, key features, specifications, reviews, and average rating. The summary should include only important and relevant information from the input. Summaries should not contain redundancies or excess information. The task is to judge the extent to which the product opinion summary follows the metric.

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

1. First, write down the steps needed to evaluate the summary according to the metric. Reiterate the metric you will be using to evaluate the summary.
2. Identify all the important and relevant information majorly discussed in the input and list them with numbering. The input includes product title, description, key features, specifications, reviews, and average rating.
3. Identify the important and relevant information present in the summary and list them with numbering.
4. Identify how many important and relevant pieces of information are present in both the summary and the input and list them with numbering.
5. Identify how many redundant, excess, or unimportant details are in the summary and list them with numbering.
6. Next, evaluate the extent to which the metric is followed.
7. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.


Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''