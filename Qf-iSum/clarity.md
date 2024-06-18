system_msg = "You are an expert in evaluating query-focused recommendation explanation summaries. These summaries are created based on a user's query and the recommended product's attributes. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a query-focused recommendation explanation summary based on the Clarity metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"

clarity_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding a recommended product for a query, including the query (entered by the user) and product title, base price, final price, product opinion summary, and the query-focused recommendation explanation summary. Your task is to evaluate and rate the query-focused recommendation explanation summary based on the given metric. Evaluate to what extent the query-focused recommendation explanation summary follows the given metric, considering the provided comprehensive information regarding the recommended product for the query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the query-focused recommendation explanation summary follows the Clarity metric.

Scores and Evaluation Criteria:

<score>1</score> - The query-focused recommendation explanation summary is garbled, lacks structure, and does not make any sense.
<score>2</score> - The query-focused recommendation explanation summary contains significant grammatical errors that hinder understanding and make it sound unnatural.
<score>3</score> - The query-focused recommendation explanation summary has errors that affect clarity or smoothness, but the main points are still comprehensible.
<score>4</score> - The query-focused recommendation explanation summary is mostly clear, with very few errors, making it easy to read and comprehend.
<score>5</score> - The query-focused recommendation explanation summary is extremely coherent, well-structured, and well-organized, providing perfect clarity.

Metric:

Clarity: Clarity measures the degree to which the information in the query-focused recommendation explanation summary is clearly presented, avoiding ambiguity and ensuring that comparisons are easy to understand. The summary should be clear, concise, and easy to comprehend, using simple language and avoiding technical jargon whenever possible. It should be well-structured and well-organized, presenting information in a straightforward manner. The metric evaluates the readability of the entire query-focused recommendation explanation summary, ensuring it is free from grammatical, spelling, punctuation, and capitalization errors. The collective quality of all sentences is considered, ensuring they build into a coherent body of information with logical organization and smooth flow between different sections and points.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the query-focused recommendation explanation summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through each sentence of the query-focused recommendation explanation summary, and give a step-by-step explanation if the query-focused recommendation explanation summary adheres to the metric considering the provided information as the input or list down if there are any clarity problems. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the query-focused recommendation explanation summary, using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First, give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''