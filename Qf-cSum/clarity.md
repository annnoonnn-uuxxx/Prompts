system_msg = "You are an expert in evaluating Comparative Explanation Summary which compares the three recommended products. The Comparative Explanation Summary is created using multiple attributes from the input. The input includes the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a Comparative Explanation Summary based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"

clarity_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding top three recommended products for a query, including query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively), using which a corresponding Comparative Explanation Summary has been generated. Your task is to evaluate and rate the Comparative Explanation Summary based on the given metric. Evaluate to what extent the Comparative Explanation Summary follows the given metric, considering the provided comprehensive information regarding top three recommended products for a query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the Comparative Explanation Summary follows the metric.


Scores and Evaluation Criteria:

<score>1</score> - The Comparative Explanation Summary completely fails to follow the Clarity metric. It is garbled, lacks structure, and does not make any sense. The Comparative Explanation Summary lacks logical flow, resulting in disjointed ideas and significant inconsistencies, making it confusing and challenging to follow.

<score>2</score> - The Comparative Explanation Summary follows the Clarity metric only to a limited extent. It contains significant grammatical errors that hinder understanding and make it sound unnatural. The Comparative Explanation Summary does not provide a clear picture of the comparison among the three products. It attempts clarity but struggles with occasional lapses in logic, clarity issues, and insufficiently connected ideas, leading to a somewhat disjointed presentation of the summary.

<score>3</score> - The Comparative Explanation Summary follows the Clarity metric to a reasonable extent. It may have errors that affect clarity or smoothness, but the main points are still comprehensible. The Comparative Explanation Summary displays a reasonable level of coherence with a logical sequence, yet occasional disruptions in flow and clarity require some improvements for a smoother transition between ideas.

<score>4</score> - The Comparative Explanation Summary mostly follows the Clarity metric. It has very few errors and is easy to read, follow, and comprehend. It provides a nearly clear picture of the comparison among the three products. The Comparative Explanation Summary demonstrates strong clarity, maintaining a clear and organized flow with effective transitions and minimal inconsistencies, effectively conveying the main points with clarity and precision.

<score>5</score> - The Comparative Explanation Summary thoroughly follows the Clarity metric. It is extremely coherent, well-structured, and well-organized, providing perfect clarity in the comparison among the three products. The Comparative Explanation Summary showcases exceptional clarity with a flawless logical flow, impeccable transitions, and consistent clarity, presenting information in an impeccably organized and easily comprehensible manner.

Metric:

Clarity: Clarity measures the degree to which the information in the Comparative Explanation Summary is clearly presented, avoiding ambiguity and ensuring that comparisons are easy to understand. The Comparative Explanation Summary should be clear, concise, and easy to comprehend, using simple language and avoiding technical jargon whenever possible. It should be well-structured and well-organized, presenting information in a straightforward manner. The metric evaluates the readability of the entire Comparative Explanation Summary, ensuring it is free from grammatical, spelling, punctuation, and capitalization errors. The collective quality of all sentences is considered, ensuring they build into a coherent body of information with logical organization and smooth flow between different sections and points. Additionally, the readability of the tabular data is assessed to ensure it clearly conveys the comparisons between three products.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the Comparative Explanation Summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through each sentence of Comparative Explanation Summary and give a step-by-step explanation if the Comparative Explanation Summary adheres to the metric considering the provided information as the input or list down if there are any clarity problems. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.


First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''