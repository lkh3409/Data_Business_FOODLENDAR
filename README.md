# Data_Business_FOODLENDAR
![dsad](https://github.com/khuda-5th/Data_Business_FOODLENDAR/assets/67497047/033e4f81-9419-4056-8764-f500e910ba92)

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **다양한 농식품들의 가장 저렴한 달을 예측해 알려주는 캘린더 서비스**

## 멤버
| 김민석 | 윤서현 | 이강훈 |
| :-: | :-: | :-: |
| <img src='https://avatars.githubusercontent.com/u/58277579?v=4' height=130 width=130></img> | <img src='https://avatars.githubusercontent.com/u/115911773?v=4' height=130 width=130></img> | <img src='https://avatars.githubusercontent.com/u/67497047?v=4' height=130 width=130></img> |

| 장유리 | 정소연 | 
| :-: | :-: |
| <img src='https://avatars.githubusercontent.com/u/115911773?v=4' height=130 width=130></img> | <img src='https://avatars.githubusercontent.com/u/115911773?v=4' height=130 width=130></img> | <img src='https://github.com/khuda-5th/CV_Face-Recognition-Attendance-Management-System/assets/160306623/745ae1ef-3c60-4199-98f2-4c0445e53ee6' height=130 width=130></img> | <img src='https://avatars.githubusercontent.com/u/115911773?v=4' height=130 width=130></img> |
<br>

## 1. 연구 배경
 ![image](https://github.com/khuda-5th/Data_Business_FOODLENDAR/assets/127953992/9d531989-3676-423c-9d22-714dd025d108)

FoodLender 프로젝트는 식비가 고민인 자취생, 특히 대학생들을 위해 언제 농수삭품이(소매가격) 가장 싼 지 예측하고, 가격을 알려주는 식자재 달력입니다.

![image](https://github.com/khuda-5th/Data_Business_FOODLENDAR/assets/127953992/f45582b6-4948-405b-a419-be64be14c4e8)
<br>
## 2. 사용 데이터
![image](https://github.com/khuda-5th/Data_Business_FOODLENDAR/assets/127953992/038bf7dd-9307-4cea-b565-32e27db2f950)

농산물 유통 정보를 종합적으로 알려주는 농넷에서 원본 데이터를 수집하였습니다.
(www.nongnet.or.kr)
<br>
## 3. 모델 설명

![image](https://github.com/lkh3409/Gram/assets/67497047/dca41573-7e7b-473f-ac78-8ca4db4e2863)


농수산물의 가격을 예측하기 위해 Meta에서 개발한 Prophet 시계열 예측 모델을 사용했습니다. Prophet 모델은 자동화된 시계열 예측 기능 제공, 손쉬운 모델링 및 예측을 가능하게 하는 장점이 있어 해당 모델을 사용하게 되었습니다. 특히 다른 시계열 모델과 달리 결측값이 있어도 모델 성능에 큰 영향을 미치지 않았으며, 이를 자동으로 처리할 수 있어 데이터 전처리가 간편했습니다. 
모델 탐색 과정에서 Prophet 모델은 ARIMA 계열 모델보다 더 우수한 성능을 보였습니다. Prophet 모델을 적용하여 장기적인 추세와 계절적 변동을 효과적으로 파악하여 예측 정확도를 높였으며, 간단한 설정만으로 강력한 예측 모델을 구축할 수 있었습니다. 이를 통해 농수산물 가격의 변동 패턴을 분석하고, 미래 가격을 예측하여 소비자의 더 나은 의사결정을 지원하고자 하였습니다.

<br>

## 4. 평가 척도
$$ MAPE = \frac{100}{n} \times \sum\limits_{i=1}^n \left\vert \frac{Y_i-\hat{Y}_i}{Y_i} \right\vert $$

$$ R^2 = 1 - \frac{\sum\limits_{i=1}^n (y_i-\hat{y})^2}{\sum\limits_{i=1}^n (y_i-\bar{y})^2} $$

모델의 성능 평가는 2023년 실제 농수산물 가격과 Prophet 모델에서 도출된 예측 결과를 비교하여 진행했습니다. 시계열 모형의 예측 성능을 평가하기 위해 **R-Squared와 MAPE (Mean Absolute Percentage Error) 지표**를 
사용했습니다. R-Squared를 활용하여 모델의 설명력을 확인하였습니다. 절댓값과 비율로 계산하여 예측 오차를 평가하는 지표인 MAPE를 활용하였고, 오차의 직관적 해석 및 단위와 무관한 평가가 이루어질 수 있도록 하였습니다. 
**MAPE 값이 10% 이하일 경우**
해당 모델을 채택하였으며, 이 기준은 분석가의 재량에 따라 결정하였습니다. 이러한 평가 척도를 통해 Prophet 모델의 예측 성능을 객관적으로 판단하고, 실제 데이터와의 비교를 통해 모델의 신뢰성을 검증하였습니다.
<br>
## 5. 결과 및 인사이트
### 5-1. 결과
100개 품목 중 평가 척도 기준을 통과한 70개 품목 선정. 그 이후 70개의 품목 중 대중성이 있는 음식들을 선별하여 FoodLendar에 표시.
### 5-2. 인사이트
- 가격에서 계절성이 나타나는 품목은 수확 시기나 제철이 존재하는 품목이었습니다.
  예) 제철 과일, 채소
- 추세만 존재하는 품목들은 2차 가공을 거치는 품목이었습니다.
  예) 간장, 두부
### 5-3. 실제 적용
완성된 FOODLENDAR의 가격과 실제 마트의 가격 비교 
![image](https://github.com/lkh3409/Gram/assets/67497047/cda55756-467f-4003-8586-79611fa4cc2d)



