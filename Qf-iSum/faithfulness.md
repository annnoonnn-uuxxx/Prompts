system_msg = "You are an expert in evaluating query-focused recommendation explanation summaries. These summaries are created based on a user's query and the recommended product's attributes. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a query-focused recommendation explanation summary based on the Faithfulness metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"



faithfulness_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding a recommended product for a query, including the query (entered by the user), product title, base price, final price, and product opinion summary, along with the query-focused recommendation explanation summary. Your task is to evaluate and rate the query-focused recommendation explanation summary based on the given metric. Evaluate to what extent the query-focused recommendation explanation summary follows the given metric, considering the provided comprehensive information regarding the recommended product for the query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the query-focused recommendation explanation summary follows the Faithfulness metric.

Scores and Evaluation Criteria:

<score>1</score> - The query-focused recommendation explanation summary contains numerous inaccuracies or fabrications or unverifiable attributes which are not present in the input. The input includes, query, product_title, base_price, final_price and product_opinion_summary.
<score>2</score> - The query-focused recommendation explanation summary includes a significant amount of hallucinated or fabricated information not present in the input data. The input includes, query, product_title, base_price, final_price and product_opinion_summary.
<score>3</score> - The query-focused recommendation explanation summary contains more than one piece of information that is not verifiable or supported by the input data. The input includes, query, product_title, base_price, final_price and product_opinion_summary.
<score>4</score> - The query-focused recommendation explanation summary contains only one piece of information that is not verifiable or supported by the input data. The input includes, query, product_title, base_price, final_price and product_opinion_summary.
<score>5</score> - Every piece of information in the query-focused recommendation explanation summary is verifiable, supported, and directly inferred from the input data. The input includes, query, product_title, base_price, final_price and product_opinion_summary.

Metric:

Faithfulness: Faithfulness measures the degree to which the information in the query-focused recommendation explanation summary is accurate, verifiable, and directly supported by the input data. The summary must faithfully represent the content provided, ensuring that all details, including the query and attributes of each product (product title, base price, final price, and product opinion summary), are correct and inferred directly from the input. Summaries will be penalized for any information that cannot be verified from the input data or for overgeneralizations.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the query-focused recommendation explanation summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through the query-focused recommendation explanation summary and list down all pieces of information in the query-focused recommendation explanation summary that are not verifiable/supported/present/inferred from the input. The input includes, query, product_title, base_price, final_price and product_opinion_summary. Give a clear step-by-step explanation of what you found.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the query-focused recommendation explanation summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First, give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''