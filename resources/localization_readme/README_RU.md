# VR Graveyard Coaster

[English](../../README.md) | Русский

Небольшой кинематографичный VR-аттракцион на Unity. Игрок сидит в вагонетке как пассажир — не как водитель — и движется по заданному маршруту через кладбище с привидениями.

![Игровой процесс](../../resources/screenshots/screenshot_gameplay_1.png)

## Возможности

- **VR-поездка по рельсам** — вагонетка движется по сплайновому пути, игрок только осматривается.
- **Зоны скорости** — триггеры вдоль трассы ускоряют и замедляют вагонетку, задавая темп поездки.
- **Поддержка динамической платформы** — вывод на кресло FutuRift по UDP на основе тангажа и крена вагонетки.
- **Порядок сцен** — стартовая сцена загружает главное меню, из которого запускается игра.

## Требования

| | |
|---|---|
| Unity | 2022.3.0f1 (URP) |
| XR | OpenXR через XR Interaction Toolkit 2.5.0 |
| Шлем | Любой PC VR-шлем с поддержкой OpenXR |

## Начало работы

1. Клонируйте репозиторий.
2. Откройте `src/Roller coaster over the grave` в Unity 2022.3.0f1.
3. Подключите VR-шлем и убедитесь, что OpenXR включён в **Project Settings → XR Plug-in Management**.
4. Откройте `Assets/Internal assets/Scenes/Bootstrap.unity` и нажмите **Play**.

## Сцены

| Сцена | Назначение |
|---|---|
| `Bootstrap` | Точка входа; сразу загружает главное меню. |
| `MainMenu` | Запуск поездки или выход. |
| `Gameplay` | Сама поездка по кладбищу. |

## Структура проекта

```
src/Roller coaster over the grave/
├─ Assets/
│  ├─ Internal assets/      # Сцены и скрипты проекта
│  │  ├─ Scenes/
│  │  └─ Scripts/
│  └─ External assets/      # Сторонние ассеты и окружение
├─ Packages/
└─ ProjectSettings/
```

## Скрипты

| Скрипт | Назначение |
|---|---|
| `Bootstrap.cs` | Загружает главное меню при запуске. |
| `MainMenuScreen.cs` | Действия главного меню. |
| `MoveAlongWaypoints.cs` | Двигает вагонетку по сплайновому пути каждый кадр. |
| `TriggerSetUpAccelerationForSpeed.cs` | Меняет множитель скорости при входе вагонетки в триггер. |
| `MoveToMainMenu.cs` | Возврат в главное меню по окончании поездки. |
| `FutuRiftControllerManager.cs` | Передаёт тангаж и крен на кресло FutuRift по UDP. |

### Настройка динамического кресла

По умолчанию `FutuRiftControllerManager` отправляет данные на `127.0.0.1:6065`. Чтобы управлять креслом на другом компьютере, измените значения `ip` и `port` в скрипте в соответствии с вашим контроллером.

## Скриншоты

<details>
<summary>Главное меню</summary>

![Главное меню](../../resources/screenshots/screenshot_main_menu.png)

</details>

<details>
<summary>Игровой процесс</summary>

![Игровой процесс](../../resources/screenshots/screenshot_gameplay_2.png)
![Игровой процесс](../../resources/screenshots/screenshot_gameplay_3.png)

</details>

<details>
<summary>Карта трассы</summary>

![Карта трассы](../../resources/screenshots/screenshot_map.png)

</details>

## Лицензия

Распространяется по [лицензии MIT](../../LICENSE.md).

Основано на оригинальном проекте Graveyard Roller Coaster от ShutovKS, используется и распространяется по лицензии MIT.
