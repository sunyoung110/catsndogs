# cats and dogs 분류기 
과적합 문제를 해결하기 위한 방법
- 이미지 어그멘테이션 (image Augmentaion )
이미지 회전 
적은 수의 이미지 데이터 셋 이용하여 정확도를 높이고 과적합 문제를 개선하는 과정이 필요 
 
 
- 순서: 1. 이미지 데이터 전처리 하기 2. 정확도와 손실 확인하기



1. 이미지 데이터 전처리 하기 
# train_datagen = ImageDataGenerator(rescale = 1.0/255.)
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
- fill_mode  : 회전 또는 이동 변환 후 빈 픽셀을 채우는 방식 지정. 디폴트 : ne
