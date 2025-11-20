# title 부산광역시 공영주차장 분포와 관광지 유동인구 분석
# 프로젝트 배경

부산광역시의 주요 관광지에는 유동인구가 많지만, 지역별로 공영 주차장 수가 충분하지 않은 불균형이 존재합니다.
본 프로젝트에서는 유동인구 데이터와 공영주차장 데이터를 결합하여 지역 간 주차 수요 불균형을 분석하고자 하였습니다.

# Dataset

부산광역시 공영주차장 정보
출처: 공공데이터포털 부산광역시_공영주차장정보조회 API
주요 변수: 위치(위경도), 주차장 규모, 총 주차면수 등

부산 관광지별 유동인구 데이터
출처: 부산관광공사
주요 변수: 관광지별 연간 유동인구 수

# 데이터 전처리 내용

일부 누락된 위경도 제거
지역 단위(구 단위)로 유동인구 집계
관광지와 주차장 데이터를 좌표 기준으로 매핑

# Methods (English)
1. Data Preprocessing

Merge population flow data with public parking lot locations.

Convert raw counts to log-transformed values to reduce skewness.

Compute parking ratio (parking lots / population flow).

2. Visualization (Folium)

Plot public parking lots as markers on a Folium map.

Generate CircleMarker layers representing parking ratio for each district.

Apply color gradients to highlight low-parking-ratio areas.

3. Statistical Analysis

Correlation analysis between population flow, number of parking lots, and parking ratio.

Multiple linear regression using log-transformed variables.

Two-sample t-test between high-ratio and low-ratio groups.

# Visualization (Folium)

지도 기반 시각화를 통해 주차장 위치 분포와 유동인구 대비 부족 지역을 직관적으로 확인.

Parking ratio가 낮은 지역은 더 진한 색으로 표시하여 공간적 위험 지역을 파악.

# Regression Analysis

Raw data: highly skewed distributions → regression not suitable.

Log transformation applied → distributions close to normal.

Multiple Linear Regression (OLS)

Dependent variable: log(parking lot count)

Independent variables: log(population flow), log(parking ratio)

R² = 0.848

Both predictors statistically significant (p < 0.01)

Hypothesis Test (t-test)


# References

공공데이터포털

부산광역시_공영주차장정보조회 Open API

부산관광공사 유동인구 데이터

Scikit-learn — Ordinary Least Squares
https://scikit-learn.org/stable/modules/linear_model.html#ordinary-least-squares
