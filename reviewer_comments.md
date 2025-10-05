# Reviewer 1

Comment to the authors
This paper presents a clear and systematic study of Indoor Positioning System (IPS) optimization in multi-floor environments using Wi-Fi RSSI fingerprinting and machine learning. The introduction of new evaluation metrics (Average Grid from Target, AGT, and Average Distance from Target, ADT) is a notable contribution, providing standardized performance measurement across varying grid sizes. The use of interpolation to simulate multiple grid resolutions from a fine-grained dataset is also a practical and scalable approach. Experimental results convincingly demonstrate that a 7x7 m grid provides an optimal trade-off between positioning accuracy and implementation feasibility, with ensemble methods (Random Forest and XGBoost) outperforming other classifiers.
Strengths:
Well-structured methodology and systematic evaluation.
Introduction of meaningful and practical evaluation metrics (AGT, ADT).
Clear presentation of experimental design, data statistics, and results.
Practical insights into grid configuration trade-offs for multi-floor IPS.
Areas for Improvement:
Novelty Positioning: The paper could better emphasize its originality in comparison with prior IPS studies, especially regarding the impact of interpolation and metric design.
Writing and Presentation: While clear overall, some sections would benefit from improved grammar, figure captions, and narrative flow. Additionally, include missing author and institutional details for completeness.
Experiment Diversity: Results are currently based on a single university building; additional environments or simulations would strengthen claims of generalizability.
Model Analysis Depth: Expand the discussion on why ensemble models outperform deep learning approaches, as this comparison is of significant interest to the research community.
Future Work: Consider exploring real-time deployment challenges, adaptive grid approaches, and transfer learning strategies to broaden impact.

# Reviewer 2
Comment to the authors
The analysis of filtering was conducted using only RF and was not extended to the other models tested. A more comprehensive analysis across all models could provide a clearer picture of the filtering method's overall effectiveness.
The author should revise the usage of past tense in the sentences.