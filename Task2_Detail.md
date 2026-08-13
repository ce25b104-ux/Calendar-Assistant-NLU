I used Bi-Directional LSTM as mentioned in the Problem Statement to solve this 
I used a 128*2 feature hidden state for this (*2 because it is Bi-Directional)
I used the hidden state at each step as the input for a nn.Linear() layer which would give me an output (Tag)  for the respective token
The Metrics I used for evaluating the results are:
   1)Token-Level Accuracy : To understand the overall efficiency of the model
   2)Per-Tag Precision/Recall/F-1 : To understand how the model is performing across different Tags
   3)Macro-F1 : To understand the average of the model across the different tags
   4)Entity-level F1: This considers a collection of tags (For example B-date+ I-date ) as one-entity and calculates the F-1 across such entities and averages them
Evaluation results:
Token Accuracy: 0.9941

Per-tag Precision / Recall:
              precision    recall  f1-score   support

           O       0.99      1.00      1.00      3846
      B-DATE       1.00      0.96      0.98       551
      I-DATE       1.00      1.00      1.00       633
      B-TIME       1.00      0.98      0.99       338
      I-TIME       0.00      0.00      0.00         0
    B-PERSON       1.00      1.00      1.00       191
    I-PERSON       0.00      0.00      0.00         0
     B-EVENT       1.00      0.99      1.00       532
     I-EVENT       1.00      0.99      1.00       227

    accuracy                           0.99      6318
   macro avg       0.78      0.77      0.77      6318
weighted avg       0.99      0.99      0.99      6318

Entity-level F1: 0.9862
