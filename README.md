# bigdata-project-w2020
# Auto Comment Generation

As we have seen  lot of codes have less comments or no comments this leads to problem in code comprehension, so it would be good if comments would be generated automatically on the basis of mining stack overflow which contains code-description mappings.These mappings can be extracted and  used to generate comments for similar code segments in other projects.However to find these descriptions we have to look at the answer with maximum votes and generate the appropriate comment using NLP, which can further be used for other similar code segments.So our training data would include these code mappings which can be used for generating comments using classification algorithms in scikit learn.
