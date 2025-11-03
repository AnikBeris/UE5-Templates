<p align="center">
  <strong>-------></strong> 
  <a href="/README_en_EN.md">English</a> | 
  <a href="/README.md">Русский</a> 
  <strong><-------</strong>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./media/logo-dark.png">
    <img alt="Project Logo" src="./media/logo-light.png" width="512" height="auto">
  </picture>
</p>

---

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-blue?style=flat&logo=github)](https://github.com/AnikBeris)
[![License](https://img.shields.io/badge/License-purple?style=flat&logo=github)](/LICENSE.md)
[![GitHub Stars](https://img.shields.io/github/stars/AnikBeris?style=flat&logo=github&label=Звёзды&color=orange)](https://github.com/AnikBeris)

</div>


<h1 align="center"> 
🚀 Создание собственного Template в Unreal Engine с кастомными настройками 
</h1> 

<h2 align="center"> 
Этот материал объясняет, как создать и настроить свой собственный <code>Template</code> в Unreal Engine 5, чтобы использовать его при создании новых проектов. 
</h2> 

<h2 align="center"> 
> 💡 Руководство предназначено для разработчиков, которые хотят ускорить процесс создания проектов, сохраняя индивидуальные настройки, папки и контент в одном шаблоне. 
</h2>




* * * * * * * * * * * * * * * * * * 
* * * * * * * * * * * * * * * * * * 



> **⚠️ Внимание отказ от ответственности:** Автор не несёт ответственности за возможные последствия.

**Если этот проект оказался полезным для Вас, вы можете оценить его, поставив звёздочку.**:star2:

<p align="left">
  <a href="https://pay.cloudtips.ru/p/7249ba98" target="_blank">
    <img src="./media/buymeacoffe.png" alt="Image">
  </a>
</p>

Пожертвования горячо приветствуются, какими бы маленькими они ни были, и большое спасибо. 😌

| | |
|-------------:|:-------------|
| **Tether USDT (BEP20)** |`0x22258ea591966e830199d27dea7c542f31ed5dc5`|
| **Bitcoin (BTC)** |`1Dbwq9EP8YpF3SrLgag2EQwGASMSGLADbh`|
| **Ethereum (ERC20)** | `0x22258ea591966e830199d27dea7c542f31ed5dc5`|
| **Binance Smart Chain (BEP20)** | `0x22258ea591966e830199d27dea7c542f31ed5dc5`|
| **Solana (SOL)** | `yYYXsiVTzsvfvsMnBxfxSZEWTGytjAViE2ojf3hbLeF`|
| **Cloud tips** | [cloudtips](https://pay.cloudtips.ru/p/7249ba98) |
| | |


* * * * * * * * * * * * * * * * * * 
* * * * * * * * * * * * * * * * * * 







## 📘 Вводная информация

Все шаблоны (`Templates`), независимо от версии Unreal Engine, хранятся в одном и том же месте:

```text
\UE_5.6\Templates
```

![](./media/Tutorial/UEFolder.png)

---

Переходим в `Templates` — здесь находятся готовые шаблоны проектов от **Epic Games**.

![](./media/Tutorial/Windows.png)

---

Для примера возьмём готовый проект из папки `TP_ThirdPersonBP` и скопируем её.

![](./media/Tutorial/OldFolder.png)

---

После копирования переименовываем папку, например, в `TP_ABGames`.

![](./media/Tutorial/NowFolder.png)

---

Переходим в созданную нами папку:

![](./media/Tutorial/CustomTemplates.png)

---

Внутри нас интересуют папки `Media` и `Config`.

- В папке **Config** находится файл `TemplateDefs.ini`, в котором хранятся настройки шаблона для Unreal Engine.

![](./media/Tutorial/Config.png)

---

## 🖼️ Переделываем изображения

В папке **Media** нужно заменить два изображения на свои.

![](./media/Tutorial/Media.png)

Пример:

| Тип | Изображение | Размер |
|:----|:-------------:|:-------------:|
| Иконка | ![TP_ThirdPersonBP](./media/Tutorial/TP_ThirdPersonBP.png) | 256×256 |
| Превью | ![TP_ThirdPersonBP_Preview](./media/Tutorial/TP_ThirdPersonBP_Preview.png) | 400×200 |

---

## ⚙️ Настраиваем `TemplateDefs.ini`

Переходим в папку `Config` и открываем файл [`TemplateDefs.ini`](./media/Tutorial/TemplateDefs.ini) в любом текстовом редакторе.  
Заменяем содержимое на следующий шаблон:

```ini
[/Script/GameProjectGeneration.TemplateProjectDefs]

Categories=Games

LocalizedDisplayNames=(Language="en",Text="От 3-го лица")
LocalizedDescriptions=(Language="en",Text="Этот шаблон содержит игрового персонажа с видом камеры от 3-го лица (через плечо). Игрок может вращать камеру и перемещаться, используя клавиатуру, мышь, геймпад или виртуальный джойстик на сенсорном устройстве. В выпадающем списке Variants можно выбрать жанровый вариант начала.")

bThumbnailAsIcon=true

ClassTypes=Character, SpringArmComponent, PlayerController, GameMode
AssetTypes=Animation Sequence, Animation Blueprint, Skeleton, Skeletal Mesh, Control Rig

FoldersToIgnore=Binaries
FoldersToIgnore=Build
FoldersToIgnore=Intermediate
FoldersToIgnore=Saved
FoldersToIgnore=Media

FilesToIgnore="%TEMPLATENAME%.uproject"
FilesToIgnore="%TEMPLATENAME%.png"
FilesToIgnore="Config/TemplateDefs.ini"
FilesToIgnore="Config/config.ini"
FilesToIgnore="Manifest.json"
FilesToIgnore="contents.txt"

FolderRenames=(From="Source/%TEMPLATENAME%",To="Source/%PROJECTNAME%")
FolderRenames=(From="Source/%TEMPLATENAME%Editor",To="Source/%PROJECTNAME%Editor")

FilenameReplacements=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME_UPPERCASE%",To="%PROJECTNAME_UPPERCASE%",bCaseSensitive=true)
FilenameReplacements=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME_LOWERCASE%",To="%PROJECTNAME_LOWERCASE%",bCaseSensitive=true)
FilenameReplacements=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME%",To="%PROJECTNAME%",bCaseSensitive=false)

ReplacementsInFiles=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME_UPPERCASE%",To="%PROJECTNAME_UPPERCASE%",bCaseSensitive=true)
ReplacementsInFiles=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME_LOWERCASE%",To="%PROJECTNAME_LOWERCASE%",bCaseSensitive=true)
ReplacementsInFiles=(Extensions=("cpp","h","ini","cs"),From="%TEMPLATENAME%",To="%PROJECTNAME%",bCaseSensitive=false)

SharedContentPacks=(MountName="LevelPrototyping",DetailLevels=("High"))
SharedContentPacks=(MountName="Characters",DetailLevels=("High"))
SharedContentPacks=(MountName="Input",DetailLevels=("High"))
EditDetailLevelPreference="High"
```

---

## 🧩 Кастомизация проекта

Запускаем исполняемый файл `TP_ThirdPersonBP.uproject` нашего шаблона.

![](./media/Tutorial/uproject.png)

После открытия проекта вносим необходимые изменения, сохраняем и закрываем его.

![](./media/Tutorial/UprojectFolders.png)

Теперь запускаем нужную версию движка, выбираем созданный шаблон — и приступаем к разработке.

![](./media/Tutorial/UEProject.png)

---

## 🏁 Итог

В результате мы получили **свой собственный шаблон** (Template) для Unreal Engine, который можно использовать для тестов и новых проектов — с уже настроенным окружением, структурой и контентом.  
Создаётся один раз, а экономит время постоянно 🚀



## 📜 Лицензия
Этот проект распространяется по [MIT License](/LICENSE).

---

Для детальной документации ознакомьтесь с **------->** [English](/README_en_EN.md) | [Русский](/README.md) **<-------**


