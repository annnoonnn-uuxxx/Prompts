system_msg = "You are an expert in evaluating comprehensive product opinion summaries. Your main task is to evaluate and assign a single score for each product summary individually, ranging from 1 to 5, based on fluency. The score must be strictly in the format: Score- <score>5</score>."


fluency_prompt_template = '''
Task Description:

{system_message}

You will be given a product opinion summary. Your task is to evaluate and rate the product opinion summary based on fluency. Evaluate to what extent the summary follows the given metric. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Metric: Fluency - The quality of the summary in terms of grammar, spelling, punctuation, capitalization, word choice, and sentence structure. The summary should contain no errors, be easy to read, follow, and comprehend.

Evaluation Criteria:

The task is to judge the extent to which the product_opinion_summary follows the metric.

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all; the summary is garbled and does not make any sense.

<score>2</score> - The metric is followed only to a limited extent; the summary has significant grammatical errors that make it hard to understand or sound unnatural.

<score>3</score> - The metric is followed to a reasonable extent; the summary has errors that affect clarity or smoothness, but the main points are comprehensible.

<score>4</score> - The metric is mostly followed; the summary has very few errors and is easy to read, follow, and comprehend.

<score>5</score> - The metric is thoroughly followed; the summary is extremely fluent, easy to read, follow, and comprehend.

Product Opinion Summary:

{Product_Opinion_Summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the product_opinion_summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through each sentence of product_opinion_summary and give a step-by-step explanation if the product_opinion_summary adheres to the metric considering the provided information as the input or list down if there are any fluency problems. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''