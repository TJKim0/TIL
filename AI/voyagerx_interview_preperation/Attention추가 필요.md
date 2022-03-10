# Attention
* Decoder 에서  출력 단어를  예측하는 매 시점(time-step) 마다 , 인코더에서  전체 입력문장을  다시한번 참고. 단, 전체 문장이 아닌 . 해당 시점에서 예측해야할 단어와 연관있는 입력단어 부분을 더 집중하게됨(가중치가 더해짐).

## Seq2Seq model 의 고질적인 문제 
* 하나의 벡터에  모든 정보를 넣으려 하니 정보 손실 문제 발생
* RNN 모델의 근본적인 문제 : Gradient Vanishing 문제

* 문장이 길어지면 번역 품질이 떨어짐 .  고로 중요한 단어에 집중하여 Decoder에 바로 전달하는 방식인 Attention 이 등장함.
* Attention 이 기존보다 더 많은 데이터를  Decoder 에 전달함.


* 참고 : transformer == encoder + decoder   /   encoder or decoder == attention + positional encoding + feedforward net

* positional encoding : attention layer 에 들어가기 전에 