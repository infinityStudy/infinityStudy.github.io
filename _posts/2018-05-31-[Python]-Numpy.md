---
layout: post
title: "[Python] Numpy 사용법"
description: Numpy 사용법 정리
image: 'https://i.imgur.com/mKy85Kr.png'
category: 'blog'
twitter_text: NUMPY Using
introduction: ,,
---

# **Numpy**
1. **ndarray(다차원배열)**
    **1.1 생성**

    * numpy.random.randn(2,3) : 2행 3열짜리 랜덤 숫자 추출
    * numpy.arange(1:5) : 1부터 5까지의 1차원 배열 생성
    * numpy.array(data1) : data1을 array로 변환

    **1.2 변환**

    * np.reshape(arr,[2,2]) : 2행2열의 2차원 배열로 변환
    * np.transpose(arr) : 2행 3열을 3행 2열로 변환

    **1.3 slicing**

    * arr = np.arange(5); 
    * arr = np.arange(1:10) : 1부터 9까지의 1차원 배열
      <결과> [1,2,3,4,5,6,7,8,9]
    * arr[5:8] : 5번째부터 7번째까지
    * arr[5:8, 1:4] # 2차원인 경우 row가 5~7, column이 1:3까지 선택
    * arr\[5][3] : 2차원인 경우 row 5번째, column 3번째인 값 선택
    * arr[0::2, 1:3] : row 0부터 2칸씩 점프하고, cols가 1~2까지인 2차원 배열 선택
    * 

    1.4 data 조회 및 비교
        * data[names == 'bob'] # 인덱스 반환
        * data[names =='bob',2:] # names가 bob인 것의 2번째 열부터 끝까지
        # data[-(names=='bob')] # names가 bob인 것은 제외하고 모두
    1.5 배열 전치와 축 바꾸기
        o **arr=np.arange(15).reshape((3,5))** : 0부터 14까지 순서대로 하는데, 3행 5열로 변환 배치한다.
        o 결과 arr을 그대로 90도 전환으로 5행3열로 만들려면, arr.T 를 한다. T는 transpose로 축을 바꾼다.
|  함수명   | 설명                                                         | 사용법                            |
| :-------: | :----------------------------------------------------------- | :-------------------------------- |
|   array   | 입력데이터를 numpy array로 변환<br>입력데이터 : list, dict, tuple,등 | numpy.array(data,dtype='float32') |
|  asarray  | 입력데이터를 ndarray로 변환                                  | numpy.asarray(data)               |
|  .dtype   | 데이터의 자료형 확인                                         | data.dtype                        |
| .astype() | 데이터의 numpy의 자료형으로 변환                             | data.astype(numpy.floadt64)       |

    

2. 계산 함수

    2.1 단항 함수 : data

|                   함수명                   | 설명                                                   | 사용법                  |
| :----------------------------------------: | :----------------------------------------------------- | :---------------------- |
|                    abs                     | 각 원소의 절대값을 구한다                              | numpy.abs(data)         |
|                    fabs                    | 원소의 절대값을 구하는데, 복소수가 아닌경우 사용한다.  | numpy.fabs(data)        |
|                    sqrt                    | 원소의 제곱근을 계산한다. arr**0.5와 같다.             | numpy.sqrt(data)        |
|                   square                   | 각원소의 게곱을 계산 arr^2                             | numpy.square(data)      |
|                    Exp                     | 각 원소의 지수 $e^x$를 구한다                          | numpy.Exp(data)         |
|            Log,log10,log2,log1p            | 각 원소의 자연로그, log10, 을 구한다.                  | numpy.log10(data)       |
|                    sign                    | 각 원소의 부호를 계산한다. 1(양수), 0, -1(음수)        | numpy.sign(data)        |
|                    ceil                    | 각 원소의 소숫자리를 올림한다.                         | numpy.ceil(data)        |
|                   floor                    | 각 원소의 소숫자리를 내린다.                           | numpy.floor(data)       |
|                    rint                    | 소수자리를 반올림한다.                                 | numpy.rint(data)        |
|                    modf                    | 각 원소의 몫과 나머지를 각각 배열로 반환한다.          | numpy.modf(data)        |
|                   isnan                    | 각원소가 숫자인지 아닌지를 나타내는 불리언 배열을 반환 | numpy.isnan(data)       |
|                  isfinite                  | 각 원소가 무한한지를 나타내는 불리언 배열 반환         | numpy.isfinite(data)    |
|                   isinf                    | 각 원고사 유한한지를 나타내는 불리언 배열 반환         | numpy.isinf(data)       |
|                cos,sin, tan                | 삼각함수 계산                                          | numpy.cos(data)         |
|              cosh, sinh, tanh              | 쌍곡삼각함수 계싼                                      | numpy.cosh(data)        |
| arccos, arccosh, arcsin, arcsinh, arctan.. | 역삼각 함수                                            | numpy.arccos(data)      |
|                logical_not                 | 각원소의 논리 부정(not) 값을 계산, -arr과 동일         | numpy.logical_not(data) |

    2.2 이항 합수 : A, B

|                함수명                | 설명                                                         | 사용법                 |
| :----------------------------------: | :----------------------------------------------------------- | :--------------------- |
|                 add                  | 두 배열에서 같은위치의 원소끼리 더한다.                      |                        |
|               subtract               | 첫번째 배열 원소에서 두번째 배열 원소를 뺀다.                |                        |
|               multiply               | 배열의 원소끼리 곱한다.                                      |                        |
|                divide                | 첫번째 배열의 요소에서 두번째 배열의 원소를 나눈다.          |                        |
|             floor_divide             | 나누기에서 몫만 취한다.                                      |                        |
|                power                 | 첫번째 배열의 원소에 두번째 배열의 원소만큼 제곱한다.        |                        |
|            maximum, fmax             | 두 원소 중 큰 값을 반환한다. fmax는 NaN을 무시               |                        |
|            minimum, fmin             | 두 원소 중 작은 값 반환, fmin은 NaN을 무시                   |                        |
|                 mod                  | 첫번째 배열의 원소에 두번째 배열의 원소를 나눈 나머지를 구한다. |                        |
|               copysing               | 첫번째 배열원소의 기호를 두번째 배열 원소의 기호로 바꾼다.   |                        |
|        greater, greater_equal        | >, >= 비교연산을 배열로 반환                                 |                        |
|           less, less_equal           | <, <= 비교연산을 배열로 반환                                 |                        |
|           equal, not_equal           | ==, != 비교연산을 배열로 반환                                |                        |
| logical_and, logical_or, logical_xor | &,                                                           | , ^의 결과를 반환한다. |


3. 주요 함수

|  함수명  | 설명                       | 사용법                                        |
| :------: | :------------------------- | :-------------------------------------------- |
| .where() | 조건 함수로 치환하는 함수  | numpy.where(a>1, 2, 0)<br>a>1이면 2, 아니면 0 |
| .sort()  | 값의 정렬, 기본은 오름차순 | data.sort()                                   |

4. 통계 함수

|     함수명     | 설명                                                        | 사용법                                      |
| :------------: | :---------------------------------------------------------- | :------------------------------------------ |
|      sum       | 모든 원소의 합을 계산한다.<br> 인자로 axis=1 사용할수 있다. | data.sum(axis=1) or numpy.sum(data, axis=1) |
|      mean      | 모든 원소의 평균 값을 구한다.                               | data.mean(axis=1)                           |
|      std       | 원소의 표준편차를 구한다.                                   | data.std()                                  |
|      var       | 원소의 분산을 구한다                                        | data.var()                                  |
|      min       | 원소의 최소값을 구한다                                      | data.min()                                  |
|      max       | 원소의 최대값을 구한다.                                     | data.max()                                  |
| argmax, argmin | 원소의 최대/최소값의 인덱스값                               | data.argmax()                               |
|     cumsum     | 원소의 누적 합, 0과 1로 옵션                                | data.cumsum(1)                              |
|    cumprod     | 원소의 누적 곱, 0과 1로 옵션                                | data.cumprod(1)                             |

5. 불리언 배열값에 대한 통계처리
    - (arr>0).sum() : True인 원소의 갯수 반환

6. 집합함수

|      함수명      | 설명                                                         | 사용법                   |
| :--------------: | :----------------------------------------------------------- | :----------------------- |
|    .unique()     | 데이터의 유일값만 반환                                       | numpy.unique(data)       |
|     .in1d()      | 첫번째 인자의 배열의 원소가 두번째 배열의 원소를 포함하는지를 비교하여 불리언으로 반환<br>in숫자1d이다. | numpy.in1d(data,[2,3,4]) |
| intersect1d(x,y) | 배열 x와 y에 공통적으로 존재하는 원소를 정렬하여 반환        | numpy.intersect1d(x,y)   |
|   union1d(x,y)   | 두 배열의 합집합을 반환한다.                                 | numpy.union1d(x,y)       |
|  setdiff1d(x,y)  | 두 배열의 차집합을 반환한다.                                 | numpy.setdiff1d(x,y)     |
|  setxor1d(x,y)   | 한 배열에는 포함되지만, 두 배열에는 포함되지 않는 원소들의 집합인 대칭차집합 반환 | numpy.setxor1d(x,y)      |


7. numpy 파일 입출력
    * np.save('파일명.npy', data) : numpy배열을 npy확장자로 저장한다.
    * np.savez('파일명.npz', a=arr1, b=arr2) : 여러개의 데이터 배열을 압축된 형태로 저장하고, a,b의 키워드로 저장됨
    * np.load('파일명') : npz의 경우는 loadDT['b'] 형태로 접근한다.
    * np.loadtxt('파일명.txt', delimiter=',') : ,구분으로 txt파일 로드

* #### np.mutmul()

  - 행렬의 곱을 계산하는 함수이다.
    > np.mutmul(npDF, npDF)

* 

$$
\begin{pmatrix} {x}1 & {y1}\\ x2 & y2 \end{pmatrix} ●\begin{pmatrix} {x}3 & {y3}\\ x4 & y4 \end{pmatrix} = \begin{pmatrix} ({x}1×x3)+(y1×x4) & (x1×y3)+(y1×y4)\\( x2×x3)+(y2×x4) & (x2×y3)+(y2×y4) \end{pmatrix}
$$

