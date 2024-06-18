system_msg = "You are an expert in evaluating comprehensive product opinion summaries created using multiple attributes from the input. The input includes product title, description, key features, specifications, reviews, and average rating. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each product individually, ranging from 1 to 5, to a summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"


sentiment_consistency_prompt_template = '''
Task Description:

{system_message}

You will be given comprehensive information about a product, including product title, description, key features, specifications, reviews, and average rating, using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the product opinion summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided comprehensive product information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the product opinion summary follows the metric.

Majority sentiment: Sentiment of majority of the users corresponding to an aspect - very positive, positive, neutral, negative and very negative.

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all while generating the summary from the input,includes product title, description, key features, specifications, reviews, and average rating, and none of the aspects present in summary have the same majority sentiment as in reviews.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the input,includes product title, description, key features, specifications, reviews, and average rating, and very few of the aspects present in summary have the same majority sentiment as in reviews.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the input,includes product title, description, key features, specifications, reviews, and average rating, and only around half of the aspects present in summary have the same majority sentiment as in reviews.

<score>4</score> - The metric is followed mostly while generating the summary from the input,includes product title, description, key features, specifications, reviews, and average rating, and most of the aspects present in summary have the same majority sentiment as in reviews.

<score>5</score> - The metric is followed thoroughly while generating the summary from the input,includes product title, description, key features, specifications, reviews, and average rating and all aspects present in summary have the same majority sentiment as in reviews.


Metric:

Sentiment Consistency - All the aspects being discussed in the summary should accurately reflect the consensus sentiment of the corresponding aspects from the reviews. Summaries should be penalized if they do not cover accurately the sentiment regarding any aspect within the summary.

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
2. Identify the aspects and their sentiments present in the summary and list them with numbering.
3. For the list of aspects identified, determine the majority sentiment from the reviews and list them with numbering.
4. Identify how many aspects and sentiments match between the reviews and the summary and list them with numbering.
5. Next, evaluate the extent to which the metric is followed.
6. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''