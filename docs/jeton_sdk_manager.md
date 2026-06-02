# Jetson Image flashing on SSD w/ NVIDIA SDK manager

## 주의 사항

* NVIDIA SDK nanager는 기본적으로 linux 기반의 tool이다. 따라서 windows system에서도 WSL을 사용한다.
  * WSL을 먼저 install 하고 진행한다.
    * powershell에서 아래 명령으로 wsl을 install 한다.

    ```powershell
    wsl --install
    ```

* WSL 환경하에서 USB port on/off를 진행하며 이 때 powershell을 사용한다.
  * powershell은 가장 최신인 7.6.x를 install 하기를 추천한다.
  * 제공한 `.msi`를 이용하여 설치 후 환경변수 `PATH`에 이 folder를 추가하고 우선권을 최상으로 한다.
  ![fig](./images/powershell_path.png)
* Downloading 과 install을 동시 진행할 경우 시간이 많이 걸린다.
  * 수업에서는 먼저 Downloading을 진행하고 시차를 두고 install을 진행한다.

## 1. SDK manager 실행하고 login 후 Download 진행

* 실행 초기화면
  ![fig1](./images/sdk_1.png)
* login click -> login on web-browser (web browser): 계정이 없으면 만들어야 함
  ![fig2](./images/sdk_2.png)
* mail을 확인하라는 message (web browser)
  ![fig3](./images/sdk_3.png)
* NVIDIA에서 보내온 메일에서 `Verify`를 눌러 검증
  ![fig4](./images/sdk_4.png)
* Email Authentication 완료
  ![fig5](./images/sdk_5.png)
* NVIDIA SDK signing 진행 (web browser)
  ![fig6](./images/sdk_6.png)
* SDK signing 완료 (web browser)
  ![fig7](./images/sdk_7.png)
* SDK login 진행
  ![fig8](./images/sdk_8.png)
* SDK login 완료 후 new version info : `Later` 선택
  ![fig9](./images/sdk_9.png)
* SDK `Step 01`
  ![fig10](./images/sdk_10.png)
** SDK `Step 01`: `Target Hardware`를 진행 -> `Jetson Orin Nano modules`
  ![fig11](./images/sdk_11.png)
* SDK `Step 02`: `TARGET COMPONENTS` 모두를 선택, `lincense`와 `Download` 선택
  ![fig12](./images/sdk_12.png)
* SDK `Step 03`: Download 진행
  ![fig13](./images/sdk_13.png)
* SDK `Step 04`
  ![fig14](./images/sdk_14.png)

## 2. SSD flashing

* Board 준비
  * image flashing 을 위해 Jetson을 `Rescue` mode로 setting
    * J14(Bustton Header) pin 10,`Force Recovery`pin을 `GND`에 jumper로 연결
  * USB port 연결

    ![fig_jetson](./images/jetson_rescue.png)
* SDK `Step 01`: 보드 연결을 자동으로 확인
  ![fig15](./images/sdk_15.png)
* SDK `Product` selection: 보드 연결이 되면 자동으로 선택 popup이 뜬다
  * `Jeson Orin Nano[8GB developer kit version]` 선택
  ![fig16](./images/sdk_16.png)
* SDK `Step 02`: `Lincese` 만 check하고 진행
  * 주의 사항: `TARGET COMPONENT` 전체 선택 확인 필수
  ![fig17](./images/sdk_17.png)
* SDK `OEM Configuration` & `Storage`: 초기 login 필요, 반드시 아래와 같이 지정한다.
  * New Username: `aidl`
  * New Password: `will`
  * Sotrage Device: `NVMe`
  * `Flash`로 다음 진행
  ![fig18](./images/sdk_18.png)
* SDK `Step 03`: `Download only` 를 unmark 하고 진행
  ![fig19](./images/sdk_19.png)
* `SDK components` install 시작 전에 확인 창이 뜬다. `Install`을 선택하고 진행
  ![fig20](./images/sdk_20.png)
* `verifying Jetson board` 후 진행 됨
  ![fig21](./images/sdk_21.png)
* SDK `Step 04`
  ![fig22](./images/sdk_22.png)


