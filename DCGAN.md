# DCGAN

* ####  Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks

  * 대부분의 환경에서 안정적으로 학습이 가능한 Convolution GAN 구조를 제안

  * Conv layer의 특정 filter들이 이미지의 특정 물체를 학습함을 보임

  * 이미지의 Sementic Quaility를 벡터 산술 연산으로 제어함. 모델이 이미지를 단순 1:1 Mapping하는것이 아님을 증명

    

* #### 등장 배경

  * 기존의 GAN은 MNIST 수준의 저화질 데이터를 생성하는것에 그치고, 고화질 데이터에 대해서는 좋은 성능을 보여주지 못함

  * 또한 두가지 모델의 minimax solution을 training하기 때문에 학습 과정이 불안정함

  * CNN 구조의 black box를 풀고자 함

    

* #### Model Architecture Approach

  * 이전에도 GAN에 Conv 구조를 적용하고자 하는 시도는 있었으나 성공적이지 못했음. 본 논문에서는 실험**(extensive)**을 통해 안정적으로 학습할 수 있는 네트워크 구조를 찾음

    1. Pooling Layer를 Strided Convolution(D)과 fractional-strided Convolution(G)로 대체

       

    2. 두 모델에 BatchNormalization 사용. 이때 모든 Layer에 사용하는것은 아니고,

       1) G의 Output Layer와,

       2) D의 Input Layer에도 사용하지 않음

       -> Gradient smoothing이 Mode Collapsing을 완화해주지만 학습의 대상이 되는 Original Image의 변질은 Generation task에 좋지 못한 영향을 끼치기 때문이 아닐까 예상됨

    3. Fully Connected Layer 제거

       

    4. Generator의 모든 활성화함수로 ReLU 사용. 이때 Output만 Tanh 사용

       

    5. Discriminator의 모든 활성화함수로 LeakyReLU 사용

       

  * **Empirical research, testing(노가다)의 결과물이기 때문에 명확한 이유를 알기 어려움**

    



* #### Experiment
