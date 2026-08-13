I used a Encoder-Decoder LSTM for this task
The hidden layer is a 512 dimension feature-map
The final cell state and hidden state of the Encoder become the initial states of the decoder
I initially tried tokenizing character by character (2026-08-13 as 2-0-2-6-0-8-1-3) and the results were miserable
Then I tokenized into Year-Month-Day-Hour-Minute format, and most importantly converted a single 'NIL' into Nil|Nil|Nil|Nil|Nil
Basically I padded the output using NIL's wherever they lacked the information, This became the turning point after which I got a much better result
I used teacher forcing for the training and validation, but did not use it for the final test
I also did not try a Bi-Directional encoder or even inputting the task-2 B-date/I-date... as I was happy with the final evaluation
The metrics I used to evaluate my models efficiency were:
  1)Overall accuracy: What percentage of times is my model giving the exact output required
  2)Class-Wise accuracy: How often is my models prediction correct across each of the classes, since I have padded NIL's each of my output has 5 continous tokens 
Final Evaluation:-
============================================================
TASK-3 EVALUATION
============================================================
Overall Exact-Match Accuracy: 90.62%
------------------------------------------------------------
Piece-wise Accuracy:
------------------------------------------------------------
YEAR   | Correct:  710 /  725 | Accuracy: 97.93%
MONTH  | Correct:  692 /  725 | Accuracy: 95.45%
DAY    | Correct:  678 /  725 | Accuracy: 93.52%
HOUR   | Correct:  711 /  725 | Accuracy: 98.07%
MINUTE | Correct:  715 /  725 | Accuracy: 98.62%
============================================================
