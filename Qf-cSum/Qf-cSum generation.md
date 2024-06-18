system_msg = "You are an expert in generating a tabular comparison among three recommended products to an user and generating a crisp and concise final verdict summary of the three recommended products on an e-commerce platform to help customers make informed purchase decisions. You will dynamically select the most important relevant attributes, features, and specifications present in all three products for contrastive comparison in tabular format. You carefully follow every instruction given to you to answer faithfully, truthfully, and accurately in the specified format."



prompt_template = """

\### Instruction:



You will always remind yourself of the role given to you in the system_msg above. As an expert, you will read each line of the prompt_template one by one slowly and follow it carefully and honestly. 



Your current task is to generate a table which compares the three recommended products based on the given user query. 



At all times you will strictly follow these seven steps below while generating the output - 



Step 1: As told you will generate a table for doing a tabular comparison for which you will first and foremost take your time and read the product_opinion_summary word-by-word of all three products and then dynamically select/choose the best and most appropriate five (5) key attributes from the product_opinion_summary. Use technical details to support the comparative analysis. Ensure that prices are mentioned in Indian Rupees (Rs.)  



Step 2: In tabular comparison, the table should have the products listed in columns of the table and the attributes you selected in Step 1 in the rows of the table. 



Step 3: Include the following attributes in your tabular comparison of three recommended products:



Product Title

Base Price (Rs.)

Final Price (Rs.)

[Attribute 1]

[Attribute 2]

[Attribute 3]

[Attribute 4]

[Attribute 5]

Average Rating

Pros

Cons



Step 4: VERY IMPORTANT - These five dynamically selected attributes in Step 3 are placeholders and should be named appropriately in the table. Do not hard-code the names of these five dynamically chosen attributes as these five dynamically chosen attributes will change as the query changes. 



Look at the below example for your reference.



Product Title

Base Price (Rs.)

Final Price (Rs.)

[Processor] 

[Display]

[Battery]

[Camera]

[RAM]

Average Rating

Pros

Cons



Note: These dynamic attribute names will change as per the query under consideration.



Step 5: If some product does not have a value/information for any of the five dynamically selected attributes, write "NA" under that product title for that attribute. 



Step 6: Base Price, Final Price, Average Rating, Pros, and Cons must be present for all the queries at any cost strictly. You cannot miss it. 



Step 7: A crisp and concise final verdict summary STRICTLY less than 100 words, providing an overview explanation of the three recommended products and their suitability for the user's needs based on the query and provide a final suggestion on which product(s) may be the best choice for the user query.



Reminder: Extract the relevant attributes dynamically from the product_opinion_summary to populate the tabular comparison and attributes should be named appropriately in the output. 



Output: Strictly write the tabular comparative summary in the following format:



Comparative Summary for [User Query]

| Attribute | Product I | Product II | Product III |

|---|---|---|---|

| Product Title | [Product 1 Title] | [Product 2 Title] | [Product 3 Title] |

| Base Price (Rs.) | [Product 1 Base Price] | [Product 2 Base Price] | [Product 3 Base Price] |

| Final Price (Rs.) | [Product 1 Final Price] | [Product 2 Final Price] | [Product 3 Final Price] |

| [Attribute 1] | [Product 1 Attribute 1] | [Product 2 Attribute 1] | [Product 3 Attribute 1] |

| [Attribute 2] | [Product 1 Attribute 2] | [Product 2 Attribute 2] | [Product 3 Attribute 2] |

| [Attribute 3] | [Product 1 Attribute 3] | [Product 2 Attribute 3] | [Product 3 Attribute 3] |

| [Attribute 4] | [Product 1 Attribute 4] | [Product 2 Attribute 4] | [Product 3 Attribute 4] |

| [Attribute 5] | [Product 1 Attribute 5] | [Product 2 Attribute 5] | [Product 3 Attribute 5] |

| Average Rating | [Product 1 Rating] | [Product 2 Rating] | [Product 3 Rating] |

| Pros | [Product 1 Pros] | [Product 2 Pros] | [Product 3 Pros] |

| Cons | [Product 1 Cons] | [Product 2 Cons] | [Product 3 Cons] |



Final Verdict Summary: [Follow instructions mentioned in Step 7 and create less than 100 word summary providing a suggestion based on the user's query and needs.]

"""



output_dict = {}



\# Iterate over the product data

for item in product_data:

  \# Extract relevant fields for each product

  query = item['query']

  products = [item[f'product{j+1}'] for j in range(3)]

   

  \# Create input prompt

  input_prompt = f"""

  {system_msg}

  {prompt_template}

  User Query: {query}

  Product I:

  Title: {products[0]['product_title']}

  Base Price: Rs. {products[0]['base_price']}

  Final Price: Rs. {products[0]['final_price']}

  Opinion Summary: {products[0]['product_opinion_summary']}

  Product II:

  Title: {products[1]['product_title']}

  Base Price: Rs. {products[1]['base_price']}

  Final Price: Rs. {products[1]['final_price']}

  Opinion Summary: {products[1]['product_opinion_summary']}

  Product III:

  Title: {products[2]['product_title']}

  Base Price: Rs. {products[2]['base_price']}

  Final Price: Rs. {products[2]['final_price']}

  Opinion Summary: {products[2]['product_opinion_summary']}

  Instructions:

1. Please go through the system_msg and strictly follow all the instructions and seven steps in the prompt_template. 
2. First and foremost take your time and read the product_opinion_summary word-by-word of all three products and then dynamically select/choose the best and most appropriate five (5) key attributes from the product_opinion_summary. 
3. The five dynamically selected attributes in Step 3 of the prompt_template are placeholders and should be named appropriately in the final output table. Do not use placeholders like [Attribute 1], [Attribute 2], [Attribute 3], [Attribute 4], [Attribute 5]. Instead, use the appropriate attribute keywords for all the queries. 
4. Base Price, Final Price, Average Rating, Pros, and Cons must be present for all the queries. 5. The Final Verdict Summary should be in less than 100 word summary providing a suggestion based on the user's query and needs. 
5. Keep the information you learned from product_opinion_summary in your memory while generating the output so that you do not make up any facts or numbers that are not verifiable or present in the input given to you. 
6. Always be faithful, truthful, and honest to the input. 

  """