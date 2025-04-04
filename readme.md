# Hackintosh EFI для Intel Core i7-13700KF и AMD Radeon RX 6900 XT (iMac Pro 2017)

Этот репозиторий содержит EFI-папку и инструкции по установке macOS (Sequoia 15.4) на компьютер с конфигурацией:

- **Процессор**: Intel® Core™ i7-13700KF (13th Gen) @ 5.4 GHz
- **Видеокарта**: AMD Radeon RX 6900 XT (16 ГБ)
- **ОЗУ**: 64 ГБ DDR5 @ up to 6000 MHz (Patriot Viper Venom 2x32ГБ DDR5 5200МГц PVV564G520C40K)
- **Материнская плата**: MSI PRO Z790-P WIFI
- **Жёсткий диск/SSD**: SSD Netac NV7000-t 512GB NT01NV7000T-512-E4X
- **macOS**: Sequoia 15.4
- **SMBIOS**: iMacPro1,1

> **Внимание**: Использование macOS на неоригинальном оборудовании не поддерживается Apple и может нарушать условия лицензионного соглашения. Все действия вы выполняете на свой страх и риск. Автор не несёт ответственности за возможные поломки оборудования или другие последствия.

---

## Содержание

1. [Описание](#описание)
2. [Требования](#требования)
3. [Настройка BIOS/UEFI](#настройка-biosuefi)
4. [Содержимое EFI](#содержимое-efi)

---

## Описание

Данный проект нацелен на успешную установку и запуск macOS Sequoia 15.4 на ПК с процессором Intel 13-го поколения (i7-13700KF) и видеокартой AMD Radeon RX 6900 XT. Система определяется как **iMacPro1,1** для обеспечения корректной работы и лучшей совместимости. 

EFI-папка настроена при помощи [OpenCore](https://github.com/acidanthera/OpenCorePkg) и необходимых кекстов (Kexts), обеспечивающих поддержку железа.

---

## Требования

1. **Совместимая материнская плата** с процессорами Intel 13-го поколения (Socket LGA1700).
2. **64 ГБ DDR5** оперативной памяти (частота 6000 MHz).
3. **AMD Radeon RX 6900 XT** (желательно референсная модель или совместимая версия).
4. **Свободный SSD/жёсткий диск** для установки macOS (рекомендуется использовать отдельный накопитель).
5. **USB-флешка** объёмом не менее 16 ГБ для создания установочного носителя.
6. **macOS** (Sequoia 15.4 или более поздняя версия, совместимая с OpenCore и вашим железом).

---

## Настройка BIOS/UEFI

Перед началом установки важно правильно настроить BIOS/UEFI. Названия пунктов могут отличаться в зависимости от производителя материнской платы.

1. **Load Optimized Defaults**: Сбросьте настройки BIOS на заводские оптимизированные.
2. **VT-d**: Отключите, если не используете виртуализацию и не планируете маппинг устройств.
3. **Secure Boot**: Отключите.
4. **Fast Boot**: Отключите.
5. **CSM (Compatibility Support Module)**: Отключите (включённый CSM может мешать загрузке UEFI).
6. **Above 4G Decoding**: Включите (особенно важно для высокопроизводительных видеокарт).
7. **XHCI Hand-off**: Включите (для корректной работы USB в macOS).
8. **Выбор основной видеокарты**: Установите приоритет на PCIe (PEG), так как у KF-версии процессора нет iGPU.

Сохраните изменения и перезагрузитесь.