system_msg = "You are an expert in evaluating comprehensive product opinion summaries. Your main task is to evaluate and assign a single score for each product summary individually, ranging from 1 to 5, based on coherence. The score must be strictly in the format: Score- <score>5</score>.\n\n"

coherence_prompt_template = '''
Task Description:

{system_message}

You will be given a product opinion summary. Your task is to evaluate and rate the product opinion summary based on coherence. Evaluate to what extent the summary follows the given metric. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Metric:

Coherence: The collective quality of all sentences. The summary should be well-structured and well-organized. It should not just be a heap of related information, but should build from sentence to sentence into a coherent body of information.

Evaluation Criteria:

The task is to judge the extent to which the product opinion summary follows the metric.

Scores and Evaluation Criteria:

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary lacks structure and logical flow, resulting in disjointed ideas and significant inconsistencies, making it confusing and challenging to follow.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary attempts coherence but struggles with occasional lapses in logic, clarity issues, and insufficiently connected ideas, leading to a somewhat disjointed presentation.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary displays a reasonable level of coherence with a logical sequence, yet occasional disruptions in flow and clarity, requiring some improvements for a smoother transition between ideas.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary demonstrates strong coherence, maintaining a clear and organized flow with effective transitions and minimal inconsistencies, effectively conveying main points with clarity and precision.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary showcases exceptional coherence with a flawless logical flow, impeccable transitions, and consistent clarity, presenting information in an impeccably organized and easily comprehensible manner.

Product Opinion Summary:

{Product_Opinion_Summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Review each sentence to ensure it is clear and logically ordered. Provide a detailed, step-by-step explanation of your findings. Highlight what is clear and what is lacking, based on the given metric. Identify and list any coherence problems. Ensure your evaluation strictly follows the specified metric.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''