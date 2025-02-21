# aimers


###수민
- 데이터 불균형(임신 성공 여부/성공:실패=1:3)로 XBboost 모델에 성공률에 더 weight를 주는 변수 "scale_pos_weight"를 추가.

'''
model_full = XGBClassifier(
    n_estimators=100,
    learning_rate=0.1,
    max_depth=6,
    random_state=42,
    scale_pos_weight=2.87,  
    eval_metric='logloss'
)
'''
- 하이퍼파라메터 튜닝 진행시 colsample_bytree': 0.8, 'learning_rate': 0.1, 'max_depth': 4, 'n_estimators': 200, 'subsample': 0.8가 최적의 파라매터라고 나옴. ROC값도 미미하게 올랐지만, 초기 소정님이 설정하셨던 파라매터가 더 결과가 좋음.
