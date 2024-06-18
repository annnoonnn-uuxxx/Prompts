system_msg = "You are an expert in evaluating the Tabular Format in Comparative Explanation Summary which compares the three recommended products. The Comparative Explanation Summary which includes Table in JSON form is created using multiple attributes from the input. The input includes the query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively). You will carefully follow every instruction in the below prompt to answer faithfully, truthfully, and accurately in the specified format. Your main task is to evaluate and assign a single score for each query individually, ranging from 1 to 5, to a correct Tabular Format presence in Tabular Format based on the given metric. The score must be strictly in the format: Score- <score>5</score>.\n\n"

tabular_format_adherence_prompt_template = '''

Task Description:

{system_message}

You will be given comprehensive information regarding top three recommended products for a query, including query (entered by the user) and product title, base price, final price, and product opinion summary (for each of the three products respectively), using which a corresponding Comparative Explanation Summary has been generated. Your task is to evaluate and rate the Tabular Format present in Comparative Explanation Summary based on the given metric. Evaluate to what extent the Tabular Format in Comparative Explanation Summary follows the given metric, considering the provided comprehensive information regarding top three recommended products for a query as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly. Strictly write the score in the given format.

Evaluation Criteria:

The task is to judge the extent to which the Comparative Explanation Summary follows the metric.


Scores and Evaluation Criteria:

<score>1</score> - The Comparative Explanation Summary completely fails to adhere to the prescribed tabular format. It lacks a tabular comparison altogether or presents the information in a highly disorganized and inconsistent manner. Dynamically selected attributes in Tabular Format are either missing or use ** placeholder** names like [Attribute 1] and so on should be examined carefully. All of the Essential attributes including Base Price, Final Price, Average Rating, Pros, and Cons are entirely absent; is not present in Tabular Format in Comparative Explanation Summary.

<score>2</score> - The Comparative Explanation Summary partially follows the tabular format but with significant deviations. The tabular comparison may be present but lacks proper structure, with inconsistencies in product and attribute placement. Some dynamically selected attributes in Tabular Format are appropriately named, while others use placeholders names like [Attribute1] or are missing. The Comparative Explanation Summary only include very few (one or two) of the essential attributes which are Base Price, Final Price, Average Rating, Pros, and Cons.

<score>3</score> - The Comparative Explanation Summary follows the tabular format to a moderate extent. The tabular comparison is present and mostly adheres to the prescribed structure, which is  products in columns and attributes in rows, but there may be minor inconsistencies or formatting issues. The majority of dynamically selected attributes are appropriately named, but a few may still use placeholders in Tabular Format. The Comparative Explanation Summary only misses very few (one or two) of the essential attributes which are Base Price, Final Price, Average Rating, Pros, and Cons.

<score>4</score> - The Comparative Explanation Summary largely adheres to the tabular format. The tabular comparison is well-structured, with products correctly listed in columns and attributes in rows. Most dynamically selected attributes are appropriately named, providing meaningful labels. All essential attributes like Base Price, Final Price, Average Rating, Pros, and Cons are present  but may have some missing or incomplete information. Only minor formatting inconsistencies or typographical errors may be observed.

<score>5</score> - The Comparative Explanation Summary strictly follows the prescribed tabular format. The tabular comparison is perfectly structured, with products precisely listed in columns and attributes in rows. All dynamically selected attributes are appropriately named, providing clear and context-specific labels. All essential attributes (Base Price, Final Price, Average Rating, Pros, and Cons) are present and complete without any omissions. The Comparative Explanation Summary demonstrates strict adherence to the specified format, ensuring a consistent and well-organized presentation of information.

Metric:

Tabular Format Adherence: The Tabular Format Adherence metric evaluates the extent to which the Comparative Explanation Summary follows the prescribed format, which includes a tabular comparison. This metric ensures that the tabular format in  Comparative Explanation Summary adheres to the specified structure, with products listed in columns and attributes in rows. It verifies that the dynamically selected attributes are appropriately named and not using any placeholders, providing meaningful and context-specific labels. Additionally, it checks for the presence of essential attributes such as Base Price, Final Price, Average Rating, Pros, and Cons, which must be included in the summary without exception.

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the tabular format in Comparative Explanation Summary as per the Tabular Format Adherence metric. Reiterate that the metric evaluates the adherence of the summary to the prescribed tabular format.
2. Check for the presence of a tabular comparison with products listed in columns and attributes in rows.
3. Ensure the table follows a consistent structure without major disorganization.
4. Verify that dynamically selected attributes in tabular format are appropriately named and free of placeholder names.
5. Confirm the presence of essential attributes: Base Price, Final Price, Average Rating, Pros, and Cons for all products.
6. Look for any minor formatting inconsistencies or typographical errors.
7. Use the evaluation criteria to assign a score within the <score></score> tags based on the extent to which the summary follows the tabular format.

Note: Strictly give the score within <score></score> tags only, e.g., Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:
'''





------



 prompt = f"""
    {system_msg}

User Query: {query}

Comparative Explanation Summary: {comparative_summary}

{tabular_format_adherence_prompt_template}
"""