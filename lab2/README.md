 ### Команды, с которыми я столкнулся в ходе выполнения работы:
| pvs |	отображение физических томов |
|---|---|
| vgs |	отображение volume group, информация об этих группах|
| lvs |	вывод информации о logical volume|
| cat /proc/mdstat |	информация о текущем raid|
| grub-install "Куда" |	установка grub|
| dd if=/dev/XXX of=/dev/YYY |	копирование одного раздела на другой x --> y|
|lsblk|	информация о дисках|
|sfdisk -d /dev/XXXX sfdisk /dev/YYY|	скопировать таблицу разделов с одного диска на другой|
|mdadm --manage /dev/md0 --add /dev/YYY|	создать raid массив (сейчас это md0)|
|mdadm --grow /dev/md63 --size=max|	изменить размер raida на max|
|mkfs.ext4 /dev/mapper/data-var_log	|форматирование раздела в файловую систему ext4|

### Данная работа состоит из 3х частей:
- настройка работоспособной системы с использованием lvm, raid
- эмуляция отказа одного из дисков
- замена дисков на лету, с добавлением новых дисков и переносом разделов.

## Задание 1
---
### Здесь мы устанавливаем и настраиваем операционную систему
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_1.png)

### Уже настроили RAID
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_2.png)

### Настроили LVM
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_3.png)

### Информация о дисках и RAID, после копирования /boot
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_4.png)
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_5.png)

## Задание 2
---
### В ходе работы отпадает один SSD, мы на ходу заменяем его и благодаря LVM сохраняем все данные и копируем на новый диск

### Информация после отключения SSD
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_6.png)
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_7.png)

### Информация о дисках после замены SSD на новый и добавления его в RAID
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_8.png)
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_9.png)

### Скопировали /boot, установили grup и выполнили перезагрузку виртуальной машины.
### В итоге все было успешно восстановлено.
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_10.png)

## Задание 3
---
### Информация о дисках и RAID была получена после удаления старого SSD 2
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_11.png)
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_12.png)

### Информация о дисках после добавления SSD 4, копирования на него файловой таблицы и перемонтирования /boot
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_13.png)

### Информация после создания нового RAID
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_14.png)

### Информация pvs до и после создания нового физического тома
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_15.png)

### Log, root и var находятся в md0
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_16.png)

### Результаты после перемещения всех LV
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_17.png)

### Удалили старый SSD, добавили новый, скопировали файловую таблицу, загрузочный раздел /boot и поставили на навый диск grub
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_18.png)

### Добавили SSD 5 в RAID и увеличили размеры разедела на обоих дисках
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_19.png)

### Увеличили размеры самого массива
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_20.png)

### Увеличили размеры VG и самих root и var, и получили конечный результат работ с SSD
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_21.png)

### Создали на HHD логический том и отформатировали их под ext4
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_22.png)

### Перемонтировали /var /log
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_23.png)

### Изменили fstab
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_24.png)

### Сняли последние pvs, lvs и vgs показания
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_25.png)

### Полная информация о дисках
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_26.png)
![alt text](https://github.com/orangejuiz/git_lab/blob/master/lab2/images/Screenshot_27.png)
