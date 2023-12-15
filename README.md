# yedam
# project
이 프로젝트는 뇌의 MRI이미지를 베이스로 한 brain_tumor를 분류하는데 scikit-learn package의 RandomForestClassifier, ExtraTreesClassifier, VotingClassifier를 활용하여 진행하였습니다.
# training dataset
MRI 데이터 셋에서 이미지를 로드하고 전처리 후 학습에 사용할 수 있는 형태로 변환하는 과정을 수행하는데 데이터셋은 'glioma_tumor', 'meningioma_tumor', 'no_tumor', 'pituitary_tumor' 네 가지 class로 구성되어있습니다. 또한 각 이미지는 64x64 픽셀 크기로 resize됩니다.
# algorithm
RandomForestClassifier, ExtraTreesClassifier, VotingClassifier를 활용하였습니다. 여러개의 의사결정 트리를 구성해 각 트리의 예측을 조합해 결과를 내기위해 RandomForestClassifier를 사용하였고 
더 극단적인 무작위성을 도입하기 위해 ExtraTreesClassifier를 사용하였습니다. 이후 각각 분류기의 예측을 결합하여 최종 예측을 하기 위해 VotingClassifier를 사용하였습니다.
# hyper-parameter of the function
RandomForestClassifier에서 트리의 최대깊이를 설정하기 위해 max_depth, 최소 샘플의 수를 결정하기 위해 min_samples_leaf와 min_samples_split를 사용하였습니다.
ExtraTreesClassifier에선 클래스의 가중치를 지정하기 위해 class_weight, 그리고 criterion로 노드의 기준을 설정하였습니다
RandomForestClassifier, ExtraTreesClassifier 모두 n_estimators를 사용해 ensemble에서 사용될 트리의 개수를 설정하였고 random_state값을 조정하였습니다.
마지막으로 VotingClassifier에서 hard를 활용해 가장 많이 선택된 클래스를 선택하게 하도록 하였습니다.
