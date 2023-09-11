# 젯슨 나노 세팅

1. sd포맷터로 sd카드 포맷
2. etcher 설치 후 sd카드 이미지를 다운받아 sd카드에 굽기
3. 젯슨 나노에 키보드, 마우스, 무선 랜 동글 등을 연결
4. 젯슨 나노 부팅 후 설정 완료

# 쿨링 팬 연결

아래 명령어를 Terminal에서 순차적으로 실행하여 젯슨 나노 업데이트 및 소프트웨어 설치
~~~shell
sudo apt-get upgrade
sudo apt-get update
sudo apt install python3-pip
sudo -H pip3 install -U jetson-stats
reboot #재부팅
jtop #젯슨 나노 상태창 열기
~~~

쿨링 팬 연결 후 아래 명령어 실행
~~~shell
cd Downloads
git clone https://github.com/jetsonworld/jetson-fan-ctl.git
cd jetson-fan-ctl
sudo sh install.sh
~~~

# CSI 카메라 연결
CSI 카메라 연결 후 아래 명령어 실행
~~~shell
git clone https://github.com/jetsonhacks/CSI-Camera.git
cd CSI-Camera
python3 simple_camera.py
~~~

# SSH 연결
~~~shell
cd ..
cd ..
ssh dli@192.168.55.1
dli
~~~
위 명령어 실행 시 Jetson nano와 연결

# Docker 설치
~~~shell
mkdir -p ~/nvdli-data # 디렉토리 추가
echo "sudo docker run --runtime nvidia -it --rm --network host \
    --volume ~/nvdli-data:/nvdli-nano/data \
    --volume /tmp/argus_socket:/tmp/argus_socket \
    --device /dev/video0 \
    nvcr.io/nvidia/dli/dli-nano-ai:v2.0.2-r32.7.1kr" > docker_dli_run.sh # 실행 파일 생성
chmod +x docker_dli_run.sh # 파일 권한 부여
./docker_dli_run.sh
~~~

192.168.55.1 접속
로그인 후 JupyterLab 접속(비밀번호: dlinano)

# Classification
1. JupyterLab 실행
2. classification 폴더의 classification_interactive.ipynb에 있는 코드들을 순서대로 실행한다.
3. 엄지를 위 아래로 향한 사진을 여러 장 촬영 후 학습

# Regression
1. JupyterLab 실행
2. regression 폴더의 regression_interactive.ipynb에 있는 코드들을 순차적으로 실행
3. 얼굴 사진을 여러 장 촬영 후 에포크 값을 조정 및 학습