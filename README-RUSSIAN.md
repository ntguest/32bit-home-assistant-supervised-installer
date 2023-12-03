[![hacs_badge](https://img.shields.io/badge/HAss-Installer-blue.svg)](https://www.home-assistant.io/)
[![Donate](https://img.shields.io/badge/donate-Pizza-yellow.svg)](https://www.buymeacoffee.com/ntguest)
[![Donate](https://img.shields.io/badge/donate-Yandex-blueviolet.svg)](https://yoomoney.ru/to/410011383527168)

# 32bit-home-assistant-supervised-installer
Home Assistant supervised and ESPHome installer for 32bit systems

## Установка Home Assistant Supervised на Debian 12 (Также для Debian 11 Bullseye)

Это руководство поможет вам установить Home Assistant Supervised практически на любой тип компьютера, включая нетбуки, неттопы и старые ПК с 32 битным процессором.

Используя Debian 12 и следуя строгому набору правил, доступных [ЗДЕСЬ](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), вы получите поддерживаемую установку Home Assistant Supervised. Если вы в любой момент решите установить дополнительное программное обеспечение для операционной системы Debian, ваша установка станет официально не поддерживаемой. Однако поддержка доступна через форумы сообщества.

*примечание: Также поддерживаются производные от Debian, такие как Armbian, ОС для Orange PI и т. д. (возможно, вам придется отредактировать /etc/os-release и заменить PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"). Ubuntu НАСТОЯТЕЛЬНО НЕ РЕКОМЕНДУЕТСЯ из-за нестабильной работы.
  


Несмотря на то, что были приложены все усилия, чтобы это руководство соответствовало [ADR-0014](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), нет гарантии работоспособности в будущем.

В этом руководстве вы будете использовать Debian 12 в качестве операционной системы. Этот тип установки называется «безголовым», и после завершения установки вам не потребуется подключать клавиатуру, мышь или монитор, хотя вы можете это сделать, если хотите.

#### Что такое Home Assistant Supervised? ####

Home Assistant - это экосистема домашней автоматизации с полным пользовательским интерфейсом, в которой работают Home Assistant Core, Home Assistant Supervisor и надстройки. Он предустановлен в ОС Home Assistant, но может быть установлен в любой системе Linux. Он использует Docker, которым управляет Home Assistant Supervisor, плюс дополнительное преимущество десятков надстроек (например, магазин приложений), которые изначально работают в среде Home Assistant.

Если вы новичок в Home Assistant, теперь вы можете перейти к Разделу 1, если вам нужна помощь в установке Debian 12. Если у вас уже установлен Debian 12 и вы хотите перейти к установке Home Assistant, перейдите к Разделу 2.





## Раздел 1 - Установка Debian

Для Debian существует [крошечный образ](https://deb.debian.org/debian/dists/Debian12.2/main/installer-i386/current/images/netboot/mini.iso), который имеет размер всего 41 мб. Там находятся самый минимум, который позволяет запустить процесс установки и скачать все необходимое из сети в процессе. Записываем его любой программой для записи образов на флешку, вставляем ее в свой ПК и устанавливаем в BIOS загрузку с USB.

<details>
  <summary> Если вам нужно пошаговое руководство по установке Debian 12 на ваш компьютер, щелкните здесь, чтобы просмотреть инструкции. </summary>


Простота процесса установки Debian позволяет в нескольких картинках показать практически все. Пробежимся бегло.
  
  
![VirtualBox_test_17_03_2021_23_31_42](https://user-images.githubusercontent.com/69485846/144154022-35236a2e-6a84-4e5e-85e7-2370dfdd71ee.png)
  
  Нажимаем Enter
  
![VirtualBox_test_17_03_2021_23_32_48](https://user-images.githubusercontent.com/69485846/144154024-7329dfda-fdd1-455b-968e-ee7dd0e3b035.png)
  
  Выбираем язык
  
![VirtualBox_test_17_03_2021_23_33_09](https://user-images.githubusercontent.com/69485846/144154025-d9ea0814-01bd-40de-b59e-08d8f25298c0.png)
  
  Страну
  
![VirtualBox_test_17_03_2021_23_33_30](https://user-images.githubusercontent.com/69485846/144154027-c37b3cf9-81c7-4f69-b3ab-e319744a940c.png)
  
  Раскладку клавиатуры
  
![VirtualBox_test_17_03_2021_23_33_44](https://user-images.githubusercontent.com/69485846/144154028-51a31699-748d-4dce-8f1a-288a03bf9055.png)
  
  Комбинацию клавиш, для переключения раскладки
  
![VirtualBox_test_17_03_2021_23_34_37](https://user-images.githubusercontent.com/69485846/144154029-db5ee106-d8c7-466f-8af0-e993d351338a.png)
  
  Придумываем прикольное имя компьютера
  
![VirtualBox_test_17_03_2021_23_35_07](https://user-images.githubusercontent.com/69485846/144154030-d293820e-fa62-4a32-a3d9-1f2d68fb4cb5.png)
  
  Жмем Enter
  
![VirtualBox_test_17_03_2021_23_35_20](https://user-images.githubusercontent.com/69485846/144154031-2e0d4668-fe6f-4629-bd05-5b3b674842fb.png)
  
  Еще раз
  
![VirtualBox_test_17_03_2021_23_42_39](https://user-images.githubusercontent.com/69485846/144154033-713cf51b-7b64-40aa-8626-187a8c4adbfd.png)
  
  Используем весь диск
  
![VirtualBox_test_17_03_2021_23_43_06](https://user-images.githubusercontent.com/69485846/144154035-707e42a5-8e14-4647-9eaa-28da3bc2dadc.png)
  
  И один раздел
  
![VirtualBox_test_17_03_2021_23_43_27](https://user-images.githubusercontent.com/69485846/144154037-19e52d60-7362-41c9-9f57-1f00109960c7.png)
  
  Записываем изменения на диск
  
![VirtualBox_test_17_03_2021_23_50_33](https://user-images.githubusercontent.com/69485846/144154040-58ea82d4-1490-40e6-8afd-14bbcec39c19.png)
  
  Я ставлю только SSH. Остальное по желанию.
  
![VirtualBox_test_17_03_2021_23_52_06](https://user-images.githubusercontent.com/69485846/144154041-7a2634c9-177b-4d19-aae0-c5eb6bc0e32b.png)
  
  И последний раз Enter
  
  
  С установкой закончили. Если я что-то и попустил, то все достаточно понятно и задокументировано в сети.
  
</details>

## Раздел 2 - Установка Home Assistant Supervised

Шаг 1: Переключитесь на учетную запись администратора и обновите систему:

```bash
su -
```
```bash
apt update && apt upgrade -y && apt autoremove && apt-get install curl -y
```

Шаг 2: Запустите скрипт установки Home Assisistant Supervised:

**ВАЖНО!!!!   Подключение должно быть ТОЛЬКО по кабелю.**

<sup>Переключиться на беспроводное соединение можно позже в разделе: Настройки - Система- Сеть</sup>


```bash
curl -sL https://hassinstall.top?token=AD7422B6E3F39BA7EE26C2FFD15880E64E0BA7F6 | bash
```

**Доступ к действующей ссылке можно получить на сайте https://hassinstall.top**. Если у Вас есть вопросы [![Donate](https://img.shields.io/badge/Спросите_в-Telegram-blue.svg)](https://t.me/avkulikoff)


Вы можете запускать скрипт без каких-либо параметров или указать явно свое устройтво с помощью опции -m :
```
qemux86
qemux86-64
qemuarm
qemuarm-64
generic-x86-64
intel-nuc
khadas-vim3
raspberrypi
raspberrypi2
raspberrypi3
raspberrypi3-64
raspberrypi4
raspberrypi4-64
yellow
tinker
odroid-c2
odroid-c4
odroid-n2
odroid-xu
opi32
opi64
opiz2
opi3lts
```  
И установить свою папку для файлов Home Assistant помощью опции -d

Пример 
```bash
curl -sL https://hassinstall.top?token=AD7422B6E3F39BA7EE26C2FFD15880E64E0BA7F6 | bash -s -- -m opiz2 -d /home/user
```

Шаг 3: После окончания выполнения скрипта необходимо перезагрузить устройство

[![Youtube](https://img.youtube.com/vi/TMbYrZFUw4w/0.jpg)](https://youtu.be/TMbYrZFUw4w)

## Раздел 3 - Установка ESPHome

<details>
  <summary> Владельцы 64-битных систем также могут идти дальше. К превеликой скорби 32-битный аддон ESPHome не существует в природе, но если вам нужен, его можно установить в виртуальное окружение. Инструкция под катом.</summary>


  Шаг 1: Установите следующие зависимости с помощью этих команд:

  ```bash  
export PATH=$PATH:/usr/sbin
apt-get install sudo python3-dev python3-venv python3-pip libffi-dev libssl-dev -y
  ```

  Шаг 2: Добавьте пользователя, папки и права:
  
  ```bash  
useradd -rm esp -G dialout
cd /srv
mkdir esp
chown esp:esp esp
  ```

  Шаг 3: Установите ESPHome 
  ```bash 
sudo -u esp -H -s
cd /srv/esp
python3 -m venv .
source bin/activate
  ```
  ```bash
python3 -m pip install wheel
export CRYPTOGRAPHY_DONT_BUILD_RUST=1
pip install cryptography==3.1.1
pip3 install esphome
exit
  ```

  Шаг 4: Добавьте рабочую папку и права

  ```bash 
cd /usr/share/hassio/homeassistant
mkdir esphome
chown esp:esp esphome
  ```
  
  Шаг 5: Создайте службу
  
  Запускаем редактор nano
  
  ```bash
nano /etc/systemd/system/esphome.service
  ```
  
  Следующий блок копируем целиком и вставляем в редактор
  
  ```
[Unit]
Description=Esphome
After=network.target
[Service]
Environment=PATH=/srv/esp/bin:/usr/sbin:/usr/bin:/sbin:/bin
Type=simple
User=root
WorkingDirectory=/usr/share/hassio/homeassistant/esphome
ExecStart=/srv/esp/bin/esphome config/ dashboard
Restart=always
[Install]
WantedBy=multi-user.target
  ```
  
  Для окончания нажмите
  
  ```
  CTRL+O, Enter и CTRL+X
  ```
  
  Активируйте службу
  ```bash
systemctl --system daemon-reload
systemctl enable esphome.service
  ```
  Панель ESPHome можно добавить как панель Lovelace iframe с адресом сервера и портом 6052
  
## В дальнейшем обновление можно делать следующими командами:

  ```bash
su -
  ```
  ```bash
sudo -u esp -H -s
cd /srv/esp
source bin/activate
pip3 install -U esphome
exit
systemctl restart esphome.service
  ```
</details>

## Теперь можно вводить пользователя и пользоваться
  
  
Ну и конечно не забываем [<img src="https://www.buymeacoffee.com/assets/img/guidelines/download-assets-2.svg" alt="BuyMeACoffee" width="100">](https://www.buymeacoffee.com/ntguest)    или    [<img src="https://hsto.org/getpro/geektimes/post_images/7a9/b88/258/7a9b882584c6ea6ed1f48e96be00a187.png" width="100">](https://yoomoney.ru/to/410011383527168)



Copyright (c) 2021-2022 Andrew V. Kulikov

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
