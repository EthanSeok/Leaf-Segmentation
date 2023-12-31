## CLIP + SAM

[SAM Pretrained Model 다운로드](https://github.com/facebookresearch/segment-anything)

* 파괴 조사시 엽면적 측정을 조금 더 편하게 하기 위한 방안을 생각하다 떠올린 아이디어.
* plantCV는 RGB값을 기반으로 초록색 부분의 면적을 산출하기 때문에 다소 부정확하였음.
* CLIP + SAM은 거의 완벽하게 segmentation이 가능했음. 
* CLIP + SAM은 다소 무거운 모델로 CUDA가 없을 경우 산출 속도가 다소 오래걸림. Jetson에 임베딩할 수 있는지는 추후 테스트해봐야 함.
* CLIP + SAM을 Jetson Nano에 임베딩한 결과 실행 시간이 30분 넘게 소요됨. (VIT_B, RN50)
* FastSAM 등 좀 더 작은 모델 사용을 고려해야 할 듯.

<br>

## 프로젝트 설명


* CLIP과 SAM을 이용하여 잎의 면적에 해당하는 마스킹 생성
* 생성한 마스크의 픽셀수를 산출
* 카메라 높이와 잎의 실제 면적을 통해 역산한 1픽셀 당 실제 면적 값을 산출하여 계산하여 잎의 면적을 추정 

![image](https://github.com/EthanSeok/Leaf-Segmentation/assets/93086581/cba08b1b-2d90-45f3-beeb-b26e0b5f2943)

결과: 5.69
실제 엽면적: 6.48

추가 calibration 필요.

<br>

## 확장

* 이후 여러 잎의 면적을 동시에 산출할 수 있는 방안을 고안하고자 함.
* Jetson Nano와 연결하여 하드웨어를 접목한 최종 엽면적 측정기를 제작하는 것이 목표.
