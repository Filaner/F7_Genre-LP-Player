# F7_Genre-LP-Player
KG 카이로스 7시 Python Proejct


## 🧠 AI Genre Analysis Engine

이 턴테이블은 단순한 재생기를 넘어, 실시간으로 음악의 지문(Fingerprint)을 분석하여 장르를 판별하는 인공지능 엔진을 탑재하고 있습니다.

### 1. 분석 파이프라인 (Analysis Pipeline)
1. **오디오 샘플링**: 곡의 특징이 가장 뚜렷한 30초 지점부터 3초간의 데이터를 추출합니다.
2. **특징 추출 (Feature Extraction)**: `Librosa` 라이브러리를 사용하여 오디오 신호에서 57개의 핵심 수치 데이터를 산출합니다.
3. **데이터 정규화 (Scaling)**: 학습 데이터와 동일한 통계적 분포를 갖도록 `StandardScaler`를 통해 데이터를 정제합니다.
4. **장르 예측 (Prediction)**: 최적화된 머신러닝 모델이 57개의 지표를 종합하여 실시간으로 장르를 결정합니다.

### 2. 추출되는 주요 오디오 특징
AI는 음악을 다음 네 가지 관점에서 분석합니다:
* **Timbral (음색)**: MFCC(Mel-frequency cepstral coefficients) 20종을 통해 목소리나 악기의 질감을 파악합니다.
* **Temporal (리듬)**: BPM(Tempo)과 Zero Crossing Rate를 통해 곡의 빠르기와 에너지를 측정합니다.
* **Spectral (주파수)**: Spectral Centroid(밝기), Rolloff 등을 통해 고음역대 분포와 음의 밝기를 분석합니다.
* **Harmonic (화성)**: Chroma 특징을 분석하여 곡의 화음 구조와 음악적 색채를 파악합니다.

### 3. 모델 시각화 (Visualizing AI Logic)

#### 피처 중요도 (Feature Importance)
모델이 장르를 판단할 때 어떤 요소에 가장 큰 비중을 두는지 보여줍니다. 예를 들어, 댄스나 힙합 장르에서는 `Tempo`와 `RMS(에너지)` 수치가 높은 중요도를 보입니다.

![Feature Importance](./feature_importance.png)

#### 데이터 정규화 (Scaling Statistics)
수집된 다양한 오디오 특징들은 각기 다른 단위를 가집니다 (예: BPM은 120대, RMS는 0.1대). AI 모델이 편향되지 않도록 `StandardScaler`를 사용해 평균 0, 표준편차 1의 상태로 변환하는 과정을 거칩니다.

![Scaler Stats](./scaler_stats.png)
