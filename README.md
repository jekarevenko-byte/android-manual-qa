# Android Manual QA: чек-лист, тест-кейсы и баг-репорты

Рабочий набор для ручного тестирования мобильного Android-приложения: от выбора объекта и чек-листа до оформления дефектов. Дополняет проект [avatar_upload_qa](https://github.com/jekarevenko-byte/avatar_upload_qa): там тест-дизайн одной функции, здесь процесс тестирования целого приложения.

> **Статус:** разделы с результатами (`test-cases/run-log.md`, `bug-reports/`) заполняются по итогам реального прогона на эмуляторе или устройстве. Файл `bug-reports/BUG-000-EXAMPLE.md` — размеченный пример оформления, а не найденный дефект.

## Объект тестирования

Выберите одно приложение и впишите его в `docs/test-object.md`. Подходят open-source приложения из [F-Droid](https://f-droid.org/) (заметки, календарь, список дел, чтения RSS): их можно устанавливать на эмулятор без аккаунтов и безопасно тестировать.

## Структура

```
android-manual-qa/
├── docs/
│   ├── test-object.md          ← приложение, версия, устройства, ограничения
│   ├── mobile-checklist.md     ← чек-лист на 60 проверок (10 категорий)
│   └── severity-priority.md    ← как назначать Severity и Priority
├── test-cases/
│   ├── test-case-template.md   ← шаблон тест-кейса
│   ├── test-cases.md           ← набор тест-кейсов (шаблон под ваше приложение)
│   └── run-log.md              ← журнал прогона: результат по каждому кейсу
├── bug-reports/
│   ├── bug-report-template.md
│   └── BUG-000-EXAMPLE.md      ← пример оформления
└── evidence/                   ← скриншоты и видео (имя: BUG-001_step3.png)
```

## Процесс

1. Установить Android Studio, создать эмулятор (Pixel, актуальная версия Android) и по возможности второй, со старой версией и малым экраном.
2. Заполнить `docs/test-object.md`.
3. Пройти чек-лист `docs/mobile-checklist.md`, отмечая результат.
4. Для найденных проблем и ключевых сценариев написать тест-кейсы из шаблона.
5. Каждый дефект оформить по `bug-reports/bug-report-template.md`, приложить скриншот/видео и лог (`adb logcat`).
6. Итоги записать в `test-cases/run-log.md`.

## Полезные команды

```bash
adb devices                                  # список устройств
adb logcat -d > evidence/logcat.txt          # сохранить лог
adb exec-out screencap -p > evidence/s.png   # скриншот
adb shell screenrecord /sdcard/bug.mp4       # запись экрана (Ctrl+C, затем adb pull /sdcard/bug.mp4)
adb shell dumpsys battery set level 5        # имитация низкого заряда
adb shell svc wifi disable                   # выключить Wi-Fi
```
