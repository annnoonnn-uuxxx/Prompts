system_msg = "You are an expert in evaluating Comparative Explanation Summary which compares the three recommended products. The Comparative Explanation Summary is created using multiple attributes from the input. The input includes the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a Comparative Explanation Summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"

faithfulness_prompt_template = '''
Task Description:

{system_message}

You will be given comprehensive information regarding top three recommended products for a query, including query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively), using which a corresponding Comparative Explanation Summary has been generated. Your task is to evaluate and rate the Comparative Explanation Summary based on the given metric. Evaluate to what extent the Comparative Explanation Summary follows the given metric, considering the provided comprehensive information regarding top three recommended products for a query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the Comparative Explanation Summary follows the metric.


Scores and Evaluation Criteria:

<score>1</score> - The Comparative Explanation Summary completely fails to follow the Faithfulness metric. The information provided is irrelevant or unrelated to the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). The Comparative Explanation Summary contains numerous inaccuracies or fabrications or unverifiable attributes.

<score>2</score> - The Comparative Explanation Summary follows the Faithfulness metric only to a limited extent. It contains very few facts that are actually verifiable or supported by the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). The Comparative Explanation Summary includes a significant amount of hallucinated or fabricated information that is not present or inferred from the input data.

<score>3</score> - The Comparative Explanation Summary reasonably follows the Faithfulness metric. However, it contains more than one piece of information that is not verifiable or supported by the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). There are some inaccuracies or overgeneralizations, but the majority of the Comparative Explanation Summary is based on the input data.

<score>4</score> - The Comparative Explanation Summary mostly follows the Faithfulness metric. It contains only one piece of information that is not verifiable or supported by the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). Most of the content is accurate, with minor issues in verifiability or consistency.

<score>5</score> - The Comparative Explanation Summary thoroughly follows the Faithfulness metric. Every piece of information in the summary is verifiable, supported, and directly inferred from the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). The Comparative Explanation Summary accurately represents the input data without any errors, fabrications, or overgeneralizations.


Metric:

Faithfulness: Faithfulness measures the degree to which the information presented in the Comparative Explanation Summary is accurate, verifiable, and directly supported by the input data. The Comparative Explanation Summary must faithfully represent the content provided, ensuring that all details, including the query and attributes of each product (product title, base price, final price, and product opinion summary), are correct and inferred directly from the input. Comparative Explanation Summary will be penalized for any information that cannot be verified from the input data or for overgeneralizations.


Evaluation Steps:

Follow the following steps strictly while giving the response:
1. First, write down the steps needed to evaluate the Comparative Explanation Summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through the Comparative Explanation Summary and list down all pieces of information in the Comparative Explanation Summary that is not verifiable/supported/present/inferred from the input. The input includes the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). Give a clear step-by-step explanation of what you found.
3. Go through the numerical consistency, particularly for the base price, final price values and average rating, to ensure that they are verifiable/supported/present/inferred from the input. The input includes the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). Give a clear step-by-step explanation of what you found.
4. Ensure that all facts, figures, and claims in the Comparative Explanation Summary are correctly represented and are verifiable/supported/present/inferred from the input data, including the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively).
5. Next, evaluate the extent to which the metric is followed.
6. Use the previous information to rate the Comparative Explanation Summary using the evaluation criteria and assign a score within the <score></score> tags.
Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.


First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''