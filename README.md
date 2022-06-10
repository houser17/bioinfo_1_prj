# bioinfo_1_prj

(★★) LIN28A binding motif predictor 만들기

목표:
LIN28A-bound sequence들로 기계학습으로 예측 모델을 만들고 평가하여 가장 performance가 좋은 motif predictor를 만드는 것

사용할 기계학습 모델 : CNN, RNN(LSTM), HMM, random forest, KNN 실시
- 사용할 library : tensorflow나 hmmlearn, sklearn, biopython
- input :  18-mer sequences that are adjacent to high-confidence binding sites (-8 to +9 from the frequently mutated base) from CLIP-35L33G.bam
- input size : 각 read별 4(# base) X 18(length) sparse matrix
- output : LIN28A-bound sequence or not(1/0)
- dataset distribution : train data : valid data : test data = 8:1:1 비율로 random하게 분배하여 사용 예정
- metrics : training시 loss나 accuracy 사용, test 시 AUC score 사용

분석 순서
- pileup에서 depth>=50, CRES(shannon entropy)>=0.8인 read를 우선 추출
- mouse fasta에서 SNP 앞 뒤 맥락 서열 18 mer를 가져와서 positive dataset으로 사용
- positive dataset의 read를 random으로 섞은 dataset을 negative dataset으로 사용
- positive, negative dataset을 정해진 비율에 맞게 겹치지 않도록 분리
- 모델 디자인 및 학습
- k-mer length에 따른 성취도 평가

고려해야 할 사항
- structure data를 고려할지
- batch size
- model hyperparameter
