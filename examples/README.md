# Examples / Примеры
English | Русский
<a name="english"></a>
# English
This directory contains a sample Module.symvers file generated for the **Tecno Pova 7 Ultra** smartphone (kernel **6.1.145**).
## Contents
 * **Module.symvers**: A ready-to-use artifact obtained by scanning the firmware dump.
   * **Device**: Tecno Pova 7 Ultra.
   * **Kernel Version**: 6.1.145.
   * **Purpose**: This file can serve as a reference for verifying the script's output or as a ready-made configuration file for setting up your build environment when developing modules for this specific kernel.
## How to use this example
You can use this file to ensure that your build system correctly recognizes kernel dependencies. Add the path to this file in your Makefile:
```makefile
# Example of integration in Makefile
KBUILD_EXTRA_SYMBOLS := $(CURDIR)/examples/Module.symvers

```

<a name="русский"></a>
# Русский
Эта директория содержит демонстрационный файл Module.symvers, сгенерированный для смартфона **Tecno Pova 7 Ultra** (ядро **6.1.145**).
## Содержимое
 * **Module.symvers**: Готовый артефакт, полученный путем сканирования дампа прошивки.
   * **Устройство**: Tecno Pova 7 Ultra.
   * **Версия ядра**: 6.1.145.
   * **Назначение**: Может быть использован в качестве эталона для проверки работы скрипта или как готовый файл для настройки окружения компиляции при разработке модулей под данное ядро.
## Как использовать этот пример
Вы можете использовать этот файл, чтобы убедиться, что ваша система сборки корректно подхватывает зависимости. Укажите путь к этому файлу в вашем Makefile:
```makefile
# Пример подключения в Makefile
KBUILD_EXTRA_SYMBOLS := $(CURDIR)/examples/Module.symvers

```
