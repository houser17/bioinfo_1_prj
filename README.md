# bioinfo_1_prj

(★★) LIN28A binding motif predictor 만들기

LIN28A-bound sequence들로 기계학습으로 예측 모델을 만들고 평가합니다. CNN이나 random forest, kNN 같은 걸 쓸 수도 있지만 단순하게 PSSM을 보정해서 쓰는 것도 가능합니다.

사용할 기계학습 모델 : RNN(LSTM), HMM 우선 기획 후 random forest 등 실시 예정
- 시계열 데이터가 input이기 때문에 이를 다루기 위한 모델을 우선적으로 사용 예정
- 사용할 library : tensorflow나 hmmlearn(or ghmm), sklearn 등
- input :  18-mer sequences that are adjacent to high-confidence binding sites (-8 to +9 from the frequently mutated base) from CLIP-35L33G.bam
- input size : each seq, 4(# base) X 18(length) sparse matrix
- output : LIN28A-bound sequence or not(1/0)
- dataset distribution : train data : valid data : test data = 8:1:1 비율로 사용 예정
- metrics : mainly AUC

분석 단계
- depth나 shannon entropy를 기준으로 cutoff 결정
- training dataset과 valid dataset을 우선 분리
- 정해진 비율에 맞게 겹치지 않도록 test set 분리
- 모델 디자인 및 학습 

추가 전망
- K-mer 개수 조절하며 
