
#
# Настройка окружения 
#

1) установить необходимые пакеты (нужны права суперпользователя)
    ./tools/setup-utils.sh
2) настроить прокси для git и wget, если нужно
    ./tools/setup-proxy.sh <username> <userpasswd>
3) скачать проект nuttx из официального репозитария разработки (в директории tmp/ хранится "чистый" проект;
   в директории src/ хранится копия содержимого tmp/ с наложенными патчами
   patch/apps-$(CONFIG_NUTTX_VERSION).patch и patch/nuttx-$(CONFIG_NUTTX_VERSION).patch)
    make setup


#
# Сборка и установка toolchain'а
#

1) собрать и установить toolchain
    make toolchain


#
# Сборка прошивки
#

1) собрать прошивку
    make configure
    make all
2) прошивка (intel-hex файл) будет находиться в директории exe/


#
# Работа с menuconfig
#

1) вызвать menuconfig
    make configure
    make menuconfig
2) произвести измения конфигурации и сохранить её как текущую конфигурацию
3) сохранить новую конфигурацию
	make configure_update


#
# Коммит проекта (исходные коды nuttx коммиту не подлежат)
#

1) создать патчи (patch/apps-$(CONFIG_NUTTX_VERSION).patch и patch/nuttx-$(CONFIG_NUTTX_VERSION).patch)
    make patch
2) осуществить коммит проекта (любым удобным способом)

