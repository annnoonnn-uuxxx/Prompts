system_msg = "You are an expert in evaluating query-focused recommendation explanation summaries. These summaries are created based on a user's query and the recommended product's attributes. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a query-focused recommendation explanation summary based on the Informativeness metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"



informativeness_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding a recommended product for a query, including the query (entered by the user), product title, base price, final price, and product opinion summary, along with the query-focused recommendation explanation summary. Your task is to evaluate and rate the query-focused recommendation explanation summary based on the given metric. Evaluate to what extent the query-focused recommendation explanation summary follows the given metric, considering the provided comprehensive information regarding the recommended product for the query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the query-focused recommendation explanation summary follows the Informativeness metric.

Scores and Evaluation Criteria:

<score>1</score> - The "query-focused recommendation explanation summary" fails to cover any of the important aspects related to the query and covers only attributes not relevant to the query.
<score>2</score> - The "query-focused recommendation explanation summary" covers only a few relevant aspects related to the query, missing most significant attributes related to the query, and includes mostly irrelevant attributes.
<score>3</score> - The "query-focused recommendation explanation summary" covers some relevant aspects related to the query, but several important attributes related to the query are missing. It includes some irrelevant attributes.
<score>4</score> - The "query-focused recommendation explanation summary" covers most relevant aspects related to the query, with minor aspects missing. It includes one or two irrelevant attributes.
<score>5</score> - The "query-focused recommendation explanation summary" comprehensively covers all relevant aspects and attributes related to the query, providing a complete and detailed explanation. It does not contain any attributes that are not relevant to the query.

Metric:

Informativeness: Informativeness evaluates the extent to which the "query-focused recommendation explanation summary" comprehensively covers all relevant aspects and attributes of the products related to the user's query, ensuring that the user feels confident that the recommended product_title is the right choice for their query. This metric assesses the presence and completeness of essential attributes in the query-focused recommendation explanation summary related only to the query entered by the user. Summaries should be penalized for missing significant aspects and rewarded for thorough coverage of the provided query.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the query-focused recommendation explanation summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. List all relevant aspects and attributes of the products in the query-focused recommendation explanation summary.
3. Check if all the listed aspects and attributes of the product are ONLY related to the user's query.
4. Note any aspects that are missing or irrelevant to the query.
5. Next, evaluate the extent to which the metric is followed.
6. Use the previous information to rate the query-focused recommendation explanation summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First, give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''