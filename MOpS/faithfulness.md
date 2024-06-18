system_msg = "You are an expert in evaluating comprehensive product opinion summaries created using multiple attributes from the input. The input includes product title, description, key features, specifications, reviews, and average rating. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each product individually, ranging from 1 to 5, to a summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"


faithfulness_prompt_template = '''
Task Description:

{system_message}

You will be given comprehensive information about a product, including product title, description, key features, specifications, reviews, and average rating, using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the product opinion summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided comprehensive product information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the product opinion summary follows the metric.

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary is for a different product and is irrelevant/unrelated to the input, which includes product title, description, key features, specifications, reviews, and average rating.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary contains very few facts actually verifiable/supported/present/inferred from the input, which includes product title, description, key features, specifications, reviews, and average rating and contains a lot of hallucinated facts.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary contains more than one piece of information that is not verifiable/present/inferred from the input, which includes product title, description, key features, specifications, reviews, and average rating.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary contains only one piece of information that is not verifiable/supported/present/inferred from the input, which includes product title, description, key features, specifications, reviews, and average rating.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and every piece of information present in the summary is verifiable/supported/present/inferred from the input, which includes product title, description, key features, specifications, reviews, and average rating.


Metric:

Faithfulness: Every piece of information mentioned in the summary should be verifiable/supported/present/inferred from the input, which includes product title, description, key features, specifications, reviews, and average rating. Summaries should be penalized if any piece of information is not verifiable/supported/present/inferred from the input or if the summary overgeneralizes something.

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


1. First write down the steps that are needed to evaluate the summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Review each sentence in summary and identify any information that cannot be verified, supported, inferred, or is not present in the input. The input includes product title, description, key features, specifications, reviews, and average rating. Provide a detailed, step-by-step explanation of your findings. Ensure your evaluation strictly follows the specified metric.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''