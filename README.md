# 영수증을 인식시켜야 해당 플레이스 리뷰 권한이 생기는 기능

사용자의 리뷰가 많아진다면,<br>
핫플레이스 판별을 위한 데이터의 증량, 절대적 이용량 증가 등 메리트가 있기에,<br>
 ‘리뷰시 할인’ 등 여러 혜택을 제공한다면 리뷰 증진에 기여한다. <br>
그러나 이러한 혜택이 제공된다면 매크로, 허위 리뷰 등 악용가능성이 있으므로,<br>
컴퓨터 비전을 통한 영수증 인식 시스템과 사용자가 로봇인지 판별하는 기능이 필요함.<br>

## Naver CLOVA 텍스트 인식 오픈소스
[Github link](https://github.com/clovaai/deep-text-recognition-benchmark)
해당 오픈소스는 PyTorch 기반 텍스트 인식 모델로, 이미지에서 영어 텍스트를 인식함.<br>
### (출처 : clovaai/deep-text-recognition-benchmark/README.md)<br>

ex)<br>
| demo images | [TRBA (**T**PS-**R**esNet-**B**iLSTM-**A**ttn)](https://drive.google.com/open?id=1b59rXuGGmKne1AuHnkgDzoYgKeETNMv9) | [TRBA (case-sensitive version)](https://drive.google.com/open?id=1ajONZOgiG9pEYsQ-eBmgkVbMDuHgPCaY) |
| ---         |     ---      |          --- |
| <img src="./demo_image/demo_1.png" width="300">    |   available   |  Available   |
| <img src="./demo_image/demo_2.jpg" width="300">      |    shakeshack    |   SHARESHACK    |
| <img src="./demo_image/demo_3.png" width="300">  |   london   |  Londen   |
| <img src="./demo_image/demo_4.png" width="300">      |    greenstead    |   Greenstead    |
| <img src="./demo_image/demo_5.png" width="300" height="100">    |   toast   |  TOAST   |
| <img src="./demo_image/demo_6.png" width="300" height="100">      |    merry    |   MERRY    |
| <img src="./demo_image/demo_7.png" width="300">    |   underground   |   underground  |
| <img src="./demo_image/demo_8.jpg" width="300">      |    ronaldo    |    RONALDO   |
| <img src="./demo_image/demo_9.jpg" width="300" height="100">    |   bally   |   BALLY  |
| <img src="./demo_image/demo_10.jpg" width="300" height="100">      |    university    |   UNIVERSITY    |


## 만약 오픈소스에 제공되지 않은 데이터셋이나, 영문이 아닌 데이터셋을 학습시키려면,
### (출처 : clovaai/deep-text-recognition-benchmark/README.md)<br>
1. Create your own lmdb dataset.
```
pip3 install fire
python3 create_lmdb_dataset.py --inputPath data/ --gtFile data/gt.txt --outputPath result/
```
The structure of data folder as below.
```
data
├── gt.txt
└── test
    ├── word_1.png
    ├── word_2.png
    ├── word_3.png
    └── ...
```
At this time, `gt.txt` should be `{imagepath}\t{label}\n` <br>
For example
```
test/word_1.png Tiredness
test/word_2.png kills
test/word_3.png A
...
```
2. Modify `--select_data`, `--batch_ratio`, and `opt.character`, see [this issue](https://github.com/clovaai/deep-text-recognition-benchmark/issues/85).

## 라이선스
Copyright (c) 2019-present NAVER Corp.
Licensed under the Apache License, Version 2.0
<br>
<br>

# 리뷰 작성자가 로봇인지 판별하는 기능

## reCAPTCHA 봇 방지 API

[Github link](https://github.com/google/recaptcha)<br>
reCAPTCHA는 오픈소스가 아닌 API 모델로, 사용자가 봇인지 판별함<br>

## 사용법

reCAPTCHA v2 -> 사용자가 이미지 클릭하여 인증<br>
reCAPTCHA v3 -> reCAPTCHA 시스템에서 사용자의 행동에 점수를 매겨 봇인지 판별 (추천)<br>

## 라이선스
BSD 
