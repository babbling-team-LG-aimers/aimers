# aimers


### 수민 수정 사항.
- 데이터 불균형(임신 성공 여부/성공:실패=1:3)로 XBboost 모델에 성공률에 더 weight를 주는 변수 "scale_pos_weight"를 추가.

```
model_full = XGBClassifier(
    n_estimators=100,
    learning_rate=0.1,
    max_depth=6,
    random_state=42,
    scale_pos_weight=2.87,  
    eval_metric='logloss'
)
```
- 하이퍼파라메터 튜닝 진행시 colsample_bytree': 0.8, 'learning_rate': 0.1, 'max_depth': 4, 'n_estimators': 200, 'subsample': 0.8가 최적의 파라매터라고 나옴. ROC값도 미미하게 올랐지만, 초기 소정님이 설정하셨던 파라매터가 더 결과가 좋음.

- 중요도 하위 20개 변수 제거시 ROC값이 증가. 다콘 결과 확인은 하지 못하였음.
### 이지 수정 사항(0226/0.7409).
- 인경님이 올려주신 catboost에서 파라미터 값만 조금 조정(4기 최우수상 수상자 파라미터값 참조).

```
cat_model = CatBoostClassifier(
    iterations=1000,
    learning_rate=0.01,
    depth=10,
    random_seed=100,
    loss_function='Logloss',
    verbose=10,
    #eval_metric= Binary f1_score,
    scale_pos_weight=3,
    one_hot_max_size=1
)

```
- iteration 200/500/1000/2000/4000 
- learning_rate 0.1/0.01/0.001 
- depth 6/10/12
- 중에서 조합한 결과 위의 조합이 가장 이상적
- ROC-AUC값이 0.7369 ->0.7374로 오름

---
## 각자 좀 어떤게 결과에 더 좋았는지 간단하게 써주시면 좋을 것 같습니다!
