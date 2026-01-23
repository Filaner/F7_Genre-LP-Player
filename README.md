# F7_Genre-LP-Player
KG 카이로스 7기 Python Proejct


## ✨ Key Features

1. Genre AI Analysis: 패턴 기반의 딥러닝 엔진을 활용하여 장르 분석 가능

2. Realistic Turntable UI: LP 회전, 톤암 이동, 레코드판 드래그를 통한 스크러빙(Scrubbing) 구현

3. Concert Mode: 실시간 Reverb 알고리즘을 적용한 입체적인 음향 효과

4. Music Library: 하위 폴더 내 음원을 자동으로 리스팅하고 관리하는 사이드바 UI

5. Dynamic Visualizer: 실시간 볼륨 레벨에 반응하는 시각 효과 및 애니메이션





## 🧠 AI Genre Analysis 1 : Statistical Feature-based Machine Learning


### 1. 분석 파이프라인 (Analysis Pipeline)
1. **오디오 샘플링**: 곡의 특징이 가장 뚜렷한 30초 지점부터 3초간의 데이터를 추출
2. **특징 추출 (Feature Extraction)**: `Librosa` 라이브러리를 사용하여 오디오 신호에서 57개의 핵심 수치 데이터를 산출
3. **데이터 정규화 (Scaling)**: 학습 데이터와 동일한 통계적 분포를 갖도록 `StandardScaler`를 통해 데이터를 정제
4. **장르 예측 (Prediction)**: 최적화된 머신러닝 모델이 57개의 지표를 종합하여 실시간으로 장르를 결정

### 2. 추출되는 주요 오디오 특징
AI는 음악을 다음 네 가지 관점에서 분석합니다:
* **Timbral (음색)**: MFCC(Mel-frequency cepstral coefficients) 20종을 통해 목소리나 악기의 질감을 파악합니다.
* **Temporal (리듬)**: BPM(Tempo)과 Zero Crossing Rate를 통해 곡의 빠르기와 에너지를 측정합니다.
* **Spectral (주파수)**: Spectral Centroid(밝기), Rolloff 등을 통해 고음역대 분포와 음의 밝기를 분석합니다.
* **Harmonic (화성)**: Chroma 특징을 분석하여 곡의 화음 구조와 음악적 색채를 파악합니다.



### 3. 모델 시각화 (Visualizing AI Logic)

#### 피처 중요도 (Feature Importance)
모델이 장르를 판단할 때 어떤 요소에 가장 큰 비중을 두는지 보여줍니다. 예를 들어, 댄스나 힙합 장르에서는 `Tempo`와 `RMS(에너지)` 수치가 높은 중요도를 보입니다.

<img width="1200" height="1000" alt="feature_importance" src="https://github.com/user-attachments/assets/82bcf29c-b3b1-4098-860f-3965ff83f4eb" />






## 🧠 AI Genre Analysis 2 : Visual Representation-based Deep Learning (CNN)

### 1. 분석 파이프라인 (Analysis Pipeline)
1. **다중 구간 샘플링**: 곡의 특징을 정확하게 분석하기 위해 10초, 30초, 50초 지점에서 각각 3초씩 총 3개의 데이터 세그먼트를 추출
2. **Mel-Spectrogram 변환**: 오디오 데이터를 2차원 이미지 데이터로 변환
3. **CNN 분석**: 스펙트로그램 이미지에서 다양한 필터를 통해 음악의 특징과 질감을 추출하여, 다수결 방식으로 최종 예측 결과를 도출
    -> 22,050Hz로 샘플링된 데이터를 128개의 Mel-bins로 시각화


<Mel-Spectrogram 예시>
<img width="1000" height="400" alt="rock_mel" src="https://github.com/user-attachments/assets/03fdff63-eece-41aa-bde4-0dc35ceed0a7" />
<img width="1000" height="400" alt="hip_hop_mel" src="https://github.com/user-attachments/assets/5a732021-d23f-4ad1-8846-ba3c124a5fdc" />

AI 2 엔진은 위 멜-스펙트로그램과 같이 소리의 주파수 밀도를 이미지로 변환하여 학습합니다. Rock 장르의 경우 저음역대의 에너지가 강한 반면, Hip-Hop은 주기적인 배음 구조를 띄는 것을 확인할 수 있습니다.


## 실행 화면

<img width="772" height="753" alt="2" src="https://github.com/user-attachments/assets/fde22e9b-e28e-4acd-ad40-229adb39a676" />


