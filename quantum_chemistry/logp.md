---
layout: page
title: logP
description: >
  partition coefficient
hide_description: true
sitemap: false
---
## log-Partition coefficient (logP)

`logP`는 octanol-water partition coefficient $$(P)$$의 $$\log$$값으로, 분자의 소수성(hydrophobicity)을 나타내는 대표 지표이다. 의약품을 설계할 때 흡수, 분포, 대사, 배설(ADME) 특성 평가에 활용한다.

### 1. Partition coefficient $$(P)$$
분배계수 $$P$$는 평형 상태에서 각 용매 속 용질의 농도 비율로 정의한다:

$$
P = \frac{[\text{solute}]_{\text{octanol}}}{[\text{solute}]_{\text{water}}}
$$

P는 무차원 지표로 몰 농도, 질량 농도 등 농도의 단위는 다양하다.

### 2. logP 값의 의미
분자의 특징은 $$\log P=0$$을 기준으로 음수이면 친수성, 양수이면 소수성으로 구분한다. 1997년 Pfizer의 Lipinski는 [Lipinski’s Rule of Five](https://doi.org/10.1016/S0169-409X(96)00423-1)에서 경구 약물들의 4가지 공통점을 찾았는데, 그 중 $$C\log P\le 5$$ 조건이 포함된다. 이는 입으로 섭취하는 경구" 약물은 소장 상피세포막의 인지질 이중층을 통과해야 체내로 흡수되는데, 이를 위해서는 상당한 소수성 (친수성에 비해 최대 10만배)을 가질 필요성을 암시한다.

### 3. logP 측정 방법

#### a. 계산적 예측법
대량 분자를 선별하기 위해서는 계산으로 logP 값을 예측하는 방법이 중요하다. 이렇게 계산(예측)된 값은 실험으로 측정한 값과 구분하기 위해 calculated-를 앞에 붙이기도 한다. (ClogP) 대표적인 계산 방법은 fragment constant와 atom-additive 방법 등이 있다.

logP 계산은 1970년대부터 이루어지고 있었다. 가장 대표적인 방법은 Hansch-Leo계열이다. 이들은 치환기(fragment)마다 기여도와 상수값을 정의하고 분자에 포함된 모든 치환기에 해당하는 기여도와 상수값을 곱하여 더하는 방식으로 분자의 logP를 계산했다.

1999년 [Wildman and Crippen](https://pubs.acs.org/doi/10.1021/ci990307l)은 68개의 원소마다 기여도를 정의하고, 원자 기여도의 합으로 logP를 계산하는 방법을 제시했다. RDkit의 `Crippen` [모듈](https://www.rdkit.org/docs/source/rdkit.Chem.Crippen.html)에는 이 파라미터들이 구현되어 있어서 편리하고 빠르게 사용할 수 있다. 특히 이 방법은 원자마다 정의된 값을 찾은 다음, 간단한 연산으로 분자의 logP를 구할 수 있기 때문에 대량의 데이터가 필요한 machine learning 분야에서 활발하게 사용하고 있다. 예를 들어 대량의 후보를 평가하거나, machine learning model의 학습 데이터나 평가 데이터를 생성할 때 유용하게 사용할 수 있다.

```python
from rdkit import Chem
from rdkit.Chem import Crippen

smiles = "CCO"
mol = Chem.MolFromSmiles(smiles)

logP = Crippeln.MolLogP(mol)
print(logP)  # -0.0014
```

#### b. 실험법
국제 표준 partition coefficient 측정 방법은 진탕 플라스크법 (shake-flask method)으로, 가장 신뢰도가 높다. 화합물을 옥탄올과 물이 들어있는 분별 깔때기에 넣고 평형에 도달할 때까지 충분히 흔든다. 각 층을 분리하여 화합물의 농도를 UV-Vis 분광법이나 HPLC 등으로 정량 분석한다. 하지만 가장 시간이 오래 걸리고 시료가 많이 필요하다.

비극성이 고정상에 오래 머무는 원리를 이용하는 reverse-phase HPLC 방법도 있다. 이미 logP를 알고 있는 표준 물질들과 retention time을 비교하여 상관관계를 이용해서 예측한다. 이 방법은 정확도는 떨어지지만, 병렬로 시료를 측정할 수 있어서 빠르다.