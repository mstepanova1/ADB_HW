# ADB_HW

1. Отобразить подключённый девайс в консоли   
```
./adb devices
```
2. Установить .apk файл приложениия todolist на телефон с компьютера через ADB
```
./adb install C:\_marie\29_QA_Vadim_Ksendzov\Lesson_ADB\todolist.apk
```
2.1. Установить приложение, если подключено несколько устройств
```
./adb -s install номер_девайса name_app.apk
```
3. Вывести адрес приложения todolist в системе Android
```
./adb shell 'pm list packages' | findstr todolist //findstr (PowerShell)
```
или
```
./adb shell 'pm list packages | grep todolist'
```
3.1. Просмотреть список приложений
```
./adb shell pm list packages
```
pm - package manager   

4. Сделать скриншот запущенного приложения todolist и сразу скопировать на компьютер в одной команде
```
./adb shell screencap -p /storage/emulated/0/DCIM/group_29.png && ./adb pull /storage/emulated/0/DCIM/group_29.png C:\_marie\29_QA_Vadim_Ksendzov\Lesson_ADB\group_29.png
```
или
```
./adb shell screencap /storage/emulated/0/DCIM/screen_name_app.png
./adb exec-out screencap -p > screen.png (скриншот сохраняется на ПК)
```
5. Вывести в консоль логи приложения todolist
```
./adb logcat -d | findstr -r todolist
```
-r - включает рекурсивный поиск в текущем каталоге  
-n - выведет номера строк, содержащих поисковый запрос  
-w - ищет весь шаблон, который находится в строке     

6. Скопировать логи приложения todolist на компьютер
```
./adb logcat -d | findstr -r todolist > todolist_29.txt
```
7. Удалить приложение todolist с телефона через ADB
```
./adb uninstall com.android.todolist
```
=====================

8. Установить старую Android-систему, Android другого производителя
```
./adb restore /Users/Name/Android/name_app/backup/backup.adb 
```
9. Создать образ из которого возможно установить (backup)
```
./adb backup -apk -shared -all -f /Users…
```
10. Перезагрузить девайс	
```
./adb reboot
```
11. Проверить подключение
```
./adb adb version
```
12. Отправить файл на девайс
```
./adb push C:\_marie\29_QA_Vadim_Ksendzov\Lesson_ADB\group_29.png /storage/emulated/0/DCIM/group_29.png
```
