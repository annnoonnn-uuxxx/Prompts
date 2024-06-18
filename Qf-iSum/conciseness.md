system_msg = "You are an expert in evaluating query-focused recommendation explanation summaries. These summaries are created based on a user's query and the recommended product's attributes. You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a query-focused recommendation explanation summary based on the Conciseness metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"



conciseness_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding a recommended product for a query, including the query (entered by the user), product title, base price, final price, product opinion summary, and the query-focused recommendation explanation summary. Your task is to evaluate and rate the query-focused recommendation explanation summary based on the given metric. Evaluate to what extent the query-focused recommendation explanation summary follows the given metric, considering the provided comprehensive information regarding the recommended product for the query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the query-focused recommendation explanation summary follows the Conciseness metric.

Scores and Evaluation Criteria:

<score>1</score> - The query-focused recommendation explanation summary is overly verbose and contains a lot of unnecessary information.
<score>2</score> - The query-focused recommendation explanation summary is somewhat verbose, with significant irrelevant details.
<score>3</score> - The query-focused recommendation explanation summary is reasonably concise but includes some unnecessary information.
<score>4</score> - The query-focused recommendation explanation summary is mostly concise, with minimal unnecessary details.
<score>5</score> - The query-focused recommendation explanation summary is very concise, with no unnecessary information, yet comprehensive in covering relevant points.

Metric:

Conciseness: Conciseness measures the degree to which the query-focused recommendation explanation summary is brief yet comprehensive, avoiding unnecessary details while covering all relevant points in strictly less than 100 words. The summary should be clear, concise, and easy to comprehend, using simple language and avoiding technical jargon whenever possible. It should be well-structured and well-organized, presenting information in a straightforward manner. The metric evaluates the readability of the entire query-focused recommendation explanation summary, ensuring it is free from unnecessary information. The collective quality of all sentences is considered, ensuring they build into a coherent body of information with logical organization and smooth flow between different sections and points.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the query-focused recommendation explanation summary as per the Conciseness metric. Reiterate what metric you will be using to evaluate the summary.
2. Review the query and summary: Carefully read and understand the user's query and the provided query-focused recommendation explanation summary.
3. Check for Word Count: Ensure the query-focused recommendation explanation summary is strictly less than 100 words. If it exceeds 100 words, it cannot score a 5.
4. Identify Unnecessary Information: Go through each sentence of the query-focused recommendation explanation summary and identify any information that is not directly relevant to the query or the recommendation. List down these unnecessary details.
5. Evaluate Coverage of Relevant Points: Ensure that all relevant aspects and attributes related to the user's query are covered in the summary. The summary should be comprehensive despite being concise.
6. Assess Overall Brevity: Determine if the summary is brief and to the point, without sacrificing the completeness of the information. The summary should effectively communicate the recommendation in a succinct manner.
7. Assign a Score: Based on the evaluation criteria, assign a score to the query-focused recommendation explanation summary within the <score></score> tags, considering the presence of unnecessary details and the overall conciseness.
8. Provide Detailed Explanation: Write a detailed explanation justifying your evaluation, highlighting any unnecessary information and assessing the comprehensiveness of the relevant points covered.
9. Format the Score: Conclude your evaluation with the score in the specified format: Score- <score>5</score>.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First, give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''