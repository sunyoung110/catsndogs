# cats and dogs 분류기 
과적합 문제를 해결하기 위한 방법
- 이미지 어그멘테이션 (image Augmentaion )
이미지 회전 
적은 수의 이미지 데이터 셋 이용하여 정확도를 높이고 과적합 문제를 개선하는 과정이 필요 
 
 
- 순서: 1. 이미지 데이터 전처리 하기 2. 정확도와 손실 확인하기



##  이미지 데이터 전처리 하기 

train_datagen = ImageDataGenerator(rescale = 1.0/255.,
                                 rotation_range=40,
                                 width_shift_range=0.2,
                                 height_shift_range=0.2,
                                 shear_range=0.2,
                                 zoom_range=0.2,
                                 horizontal_flip=True,
                                 fill_mode='nearest')
- ImageDataGenerator의 rescale 파라미터 값을 1.0/ 255로 지정하면 모든 값을 255로 나눔
- rotation_range : 이미지를 임의로 회전시키는 각도 지정 0-180
- width_shift, height_shift : 이미지를 임의로 수직 또는 수평 방향으로 이동시키는 범위 지정 
- shear_range : 전단 변환을 위한 파라미터 , 이미지를 어긋나 보이도록 변환 
- zoom_range : 이미지를 임의로 확대하는 정도 
- horizontal_flip : 이미지를 임의로 뒤집을지 여부를 결정
- fill_mode  : 회전 또는 이동 변환 후 빈 픽셀을 채우는 방식 지정. 디폴트 : nearest

### 결과 : 
1.훈련 데이터, 테스트 데이터에 대한 정확도, 손실 값이 일치하는 경향 보임. 
과적합 현상이 두드러지게 감소했음.
2. 최종 정확도 0.80 은 이미지 어그멘테이션을 사용하지 않은 경우의 훈련 데이터에 대한 정확도 보다 감소.


--> 이미지 어그멘테이션 기법을 적용하면 ,
- 메모리 저장 공간 차지하지 않고,
- 적은 수의 이미지 데이터로 매우 다양한 훈련데이터를 사용하는 효과가 있음.
- 하지만 훈련 시간이 증가 ( 즉시 이미지 프로세싱이 이루어지기 때문에)
