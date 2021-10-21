# human_following_bot

NVIDIA의 Jetson Nano에 카메라를 연결하고 Real-time object detection을 수행한다. 얻어진 Bounding Box중 Person으로 분류된 Box의 좌표를 확인하고 해당 좌표가 중앙에 오도록 자동차의 모터를 이용해 조향각을 조절하고 앞으로 전진하여 사람을 따라가도록 한다.

# OS Installation

Jetson Nano를 사용하기 위해서는 JetPack이라고 불리는 OS를 보드에 설치해야 한다. JetPack은 https://developer.nvidia.com/embedded/jetpack에서 다운로드 받을 수 있다. 각자의 보드에 맞는 JetPack을 다운로드 받아 Etcher, Rufus와 같은 툴을 이용하여 Jetson 보드의 SD카드에 플래시해 준다. 이후 처음 부팅시 뜨는 안내에 따라 초기설정을 진행하면 된다. 언어 설정은 영어로 하는것을 추천.

# SW

Ctrl+Alt+T를 눌러 터미널 창을 하나 띄우고 다음과 같이 입력한다.
```
sudo apt-get update
sudo apt-get install git cmake libpython3-dev python3-numpy
git clone --recursive https://github.com/dusty-nv/jetson-inference
cd jetson-inference
mkdir build
cd build
cmake ../
```

한줄씩 입력하여 작업이 완료되면 다음 줄을 입력한다 . 마지막줄을 입력하면 아래와 같은 창이 뜬다.
![download-models](https://user-images.githubusercontent.com/75787789/138288534-2aec921b-dccf-4c82-9c56-06bbde0013aa.jpg)

꼭 필요한 것은 Object Detection의 SSD-Mobilenet-v2이므로 이것만 체크하고 Ok를 눌러 진행해도 무방하다. 다른 Model을 사용해 보고 싶다면 사용할 것을 체크하여 진행하면 된다.

Model 다운로드가 완료된 후 아래와 같은 Pytorch 설치화면이 뜨는데 Pytorch 또한 꼭 필요한 것은 아니므로 개인적으로 필요한 사람만 선택하여 설치하면 된다.
![pytorch-installer](https://user-images.githubusercontent.com/75787789/138288872-d96a6326-9654-4377-9c03-f444e7063d9a.jpg)

