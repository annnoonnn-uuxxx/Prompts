# "This Suits You the Best": Query Focused Product Comparison Summary

## Abstract

Existing recommendation systems often struggle to provide users with the comparative insights necessary for informed decision-making among recommended items. To address this challenge, we introduce **Query Focused Product Comparison Summary (Qf-PCS)**, a novel framework that leverages state-of-the-art open-source Large Language Models (LLMs) to generate **Query-Focused Comparative Summaries (Qf-cSum)** and **Query-Focused Individual Summaries (Qf-iSum)** using **Multi-source Product Opinion Summaries (MOpS)**.

Our approach dynamically selects the most relevant attributes for comparing already recommended products based on user queries, eliminating the need for predefined category-specific templates. We present a new benchmark dataset, **Flipkart-1000-Q2P**, and conduct extensive experiments using various LLMs across three phases. Evaluation is performed using both reference-free and reference-based metrics, alongside human annotation.

Results demonstrate the effectiveness of Qf-PCS in generating clear, informative, and concise summaries that enhance user decision-making without requiring visits to multiple sources of information. Evaluations show that Qf-PCS produces high-quality, clear, and relevant summaries with significant speed and memory efficiency improvements, making it practical for real-world applications. Our framework is a recommendation engine and category-agnostic, maintaining user privacy by solely relying on user queries and product information.
