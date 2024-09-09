경진대회 baseline 코드를 바탕으로 기존에 있던 RandomForest Regressor 에
Linear, XGBoost, MLP Regressor를 사용하고 각 모델의 하이퍼파라미터를 최적으로 하여 
검증데이터의 r2_score를 최대한 높이는 방향으로 훈련한 결과,

	            RandomForest	  Linear	        XGBoost	        MLP
Train 	      0.951	          0.989	          0.934	          0.973
Validation	  0.700	         -1.236	          0.728	          0.693

대부분의 경우 Overfitting 이 일어나는 것을 볼 수 있었습니다.
이를 해소하려면 모델복잡도를 낮추거나 데이터를 증강해야 하는데,
하이퍼파라미터 튜닝시에 모두 L2-regularization 를 최상으로 해 주었기 때문에,
Transformer류의 특별한 모델을 쓰는 것이 아니라면 더 이상 모델 복잡도를 높이는 것은 의미가 없으며,
훈련 데이터수를 늘려야만 한다.

그러므로 정확도를 높이기 위해 이제 남은 방법은, 
IRAK4 효소에 대한 저해제 물질들의 SMILES와 IC50 값을 담은 또 다른 데이터셋을 찾아내어,
그것을 기존의 데이터셋과 합쳐서 재전처리 및 훈련하는 것이다. 
