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

쿨링팬 연결 후 아래 명령어 실행
~~~shell
cd Downloads
git clone https://github.com/jetsonworld/jetson-fan-ctl.git
cd jetson-fan-ctl
sudo sh install.sh
~~~