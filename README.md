🔑 **PRT(Peer Review Template)** (리뷰어 : 김성연)

- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요? (완성도)**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 부분의 코드 및 결과물을 캡쳐하여 사진으로 첨부
     
### 전처리 관련 코드
![review_img1](https://github.com/Democratas/My-first-repository/assets/83098550/89ea23e4-77ef-4ae3-addc-8eb3b54ccb01)
### Loss가 안정적으로 잘 떨어지는 것을 볼 수 있습니다.
![Screenshot 2024-07-09 at 6 05 10 PM](https://github.com/Democratas/My-first-repository/assets/83098550/3ce604ef-bdb8-4a45-9100-f195dbaca2a2)

- [ ]  **2. 프로젝트에서 핵심적인 부분에 대한 설명이 주석(닥스트링) 및 마크다운 형태로 잘 기록되어있나요? (설명)**
    - [ ]  모델 선정 이유
    - [ ]  Metrics 선정 이유
    - [ ]  Loss 선정 이유

- [ ]  **3. 체크리스트에 해당하는 항목들을 모두 수행하였나요? (문제 해결)**
    - [ ]  데이터를 분할하여 프로젝트를 진행했나요? (train, validation, test 데이터로 구분)
    - [ ]  하이퍼파라미터를 변경해가며 여러 시도를 했나요? (learning rate, dropout rate, unit, batch size, epoch 등)
    - [ ]  각 실험을 시각화하여 비교하였나요?
    - [ ]  모든 실험 결과가 기록되었나요?

- [ ]  **4. 프로젝트에 대한 회고가 상세히 기록 되어 있나요? (회고, 정리)**
    - [ ]  배운 점
    - [ ]  아쉬운 점
    - [ ]  느낀 점
    - [ ]  어려웠던 점

## 리뷰
- 코드를 깔끔하게 잘 짜셔서 인상깊었습니다
- 저도 전체적으로 코드를 다시 정리하는 시간을 가져야 겠다는 다짐을 하게 되었습니다. 고생많으셨습니다 !

## 추가 코드 수정 제안
![Screenshot 2024-07-09 at 6 07 49 PM](https://github.com/Democratas/My-first-repository/assets/83098550/7dbc4122-cb94-4b11-bfac-5251e7509599)
이 부분에서 오류가 나신것으로 보입니다.

이부분을
```python
inputs = [inp_lang_tokenizer.word_index[i] for i in mecab.morphs(sentence)]
inputs = tf.keras.preprocessing.sequence.pad_sequences([inputs], maxlen=max_length_inp, padding='post')
```
이렇게 수정하시면 될 것 같습니다
```python
inputs = inp_lang_tokenizer.texts_to_sequences([mecab.morphs(sentence)])
inputs = tf.keras.preprocessing.sequence.pad_sequences(inputs, maxlen=max_length_inp, padding='post')
```
