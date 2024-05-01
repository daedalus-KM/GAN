# GAN
적대적 생성 신경망(GAN)이란

1. GAN이란?
   GAN(Generative Adversarial Network)이란 두개의 네트워크가 적대적으로 학습되며 데이터를 생성하는 구조이다.
   가장 흔히 비유되는 예시로는 경찰과 위조지폐범을 예시로 들 수 있다. 위조지폐범은 경찰이 구분할 수 없도록 진짜 같은 위조지폐를 만드려고 노력하고,
   경찰은 위조지폐범이 만든 가짜 지폐를 잘 구분하기 위해 노력한다.
   GAN에서는 Generator가 위조지폐범의 역할로서 진짜같은 가짜 데이터를 생성하며, Discriminator는 Generator가 생성한 가짜 데이터와 진짜 데이터를 분류한다.

 
3. Loss Function
   
   ![image](https://github.com/daedalus-KM/GAN/assets/85052989/613767a6-b13d-4b2b-a645-2b06f419f90c)
   
   
   간단하게 설명하면, Generator는 해당 Loss function을 최소화 시키려고 하고, Discriminator는 최대화 시키려고 한다.

   
   2-1. First term
      첫번째 항은 진짜 데이터 x를 Discriminator의 입력으로 사용하였을 때의 결과에 log를 취한 기댓값이다.
      Discriminator가 해당 Loss를 최대화 시키려고 한다면,
      진짜 데이터에 대해 진짜라고 예측(1을 출력)해야 첫번째 항이 0으로서 최댓값이 된다. (D(x)는 0~1사이의 값을 출력하기 때문)

   
   2-2. Second term
      두번째 항은 Discriminator가 random noise z를 입력으로 받은 Generator의 출력을 입력으로 사용하는데,
      Loss를 최대화 시키려는 Discriminator의 입장에서는 Generator가 생성한 가짜 데이터를 가짜라고 예측(0을 출력)해야
      두번째 항이 0으로서 최댓값이 된다.
   
      하지만 Loss를 최소화 시켜야 하는 Generator입장에서는 본인이 생성한 가짜 데이터를 Discriminator가 진짜라고
      예측(Discriminator가 1을 출력)해야 두번째 항이 최소가 된다.
      Generator는 이때 MSE, SSE등의 loss를 사용할 수 있고, Discriminator는 binary classification이므로 binary cross entropy를 사용하는 것이 일반적이다.
      
Referneces
1. https://velog.io/@hyebbly/Deep-Learning-Loss-%EC%A0%95%EB%A6%AC-1-GAN-loss
2. https://baechu-story.tistory.com/12
