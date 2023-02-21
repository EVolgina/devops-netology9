# Задание
# С помощью базового файла конфигурации запустите Ubuntu 20.04 в VirtualBox посредством Vagrant:

# Создайте директорию, в которой будут храниться конфигурационные файлы Vagrant. В ней выполните vagrant init. Замените содержимое Vagrantfile 
по умолчанию следующим:\
 Vagrant.configure("2") do |config|\
 	config.vm.box = "bento/ubuntu-20.04"\
 end\
# Выполнение в этой директории vagrant up установит провайдер VirtualBox для Vagrant, скачает необходимый образ и запустит виртуальную машину.
![Установка](https://github.com/EVolgina/devops-netology9/blob/main/vagraninst.png)
# vagrant suspend выключит виртуальную машину с сохранением ее состояния (т.е., при следующем vagrant up будут запущены все процессы внутри, 
которые работали на момент вызова suspend), vagrant halt выключит виртуальную машину штатным образом.
# Ознакомьтесь с графическим интерфейсом VirtualBox, посмотрите как выглядит виртуальная машина, которую создал для вас Vagrant, 
какие аппаратные ресурсы ей выделены. Какие ресурсы выделены по-умолчанию?
![Виртуальная машина](https://github.com/EVolgina/devops-netology9/blob/main/virt.png)
# Ознакомьтесь с возможностями конфигурации VirtualBox через Vagrantfile: документация. Как добавить оперативной памяти или ресурсов процессора виртуальной машине?
ответ: Внесла изменения в файл Vagrantfile\
config.vm.provider "virtualbox" do |vb|\
	vb.name="lern"\
end\
	config.vm.provider "virtualbox" do |vb|	\
	vb.memory=2048\
	vb.cpus=1\
 end\
![Виртульная машина с параметрами](https://github.com/EVolgina/devops-netology9/blob/main/virtconfig.png)
# Команда vagrant ssh из директории, в которой содержится Vagrantfile, позволит вам оказаться внутри виртуальной машины без каких-либо дополнительных настроек. Попрактикуйтесь в выполнении обсуждаемых команд в терминале Ubuntu.
# По SSH подключилась к виртуальной машине
Ознакомьтесь с разделами man bash, почитайте о настройках самого bash:
man bash\
какой переменной можно задать длину журнала history, и на какой строчке manual это описывается?\
ответ:         задаётся переменой окружения HISTSIZE, она описана со строки    -827 строка\
что делает директива ignoreboth в bash?\
ответ: не записывает команду Которая начинается с пробела, либо команду которая дублирует предыдущую. \

# В каких сценариях использования применимы скобки {} и на какой строчке man bash это описано?
ответ: то что находится в фигурных скобках выполняется в контексте текущей оболочки и занимает меньше ресурсов\
при работе с массивами, строка с 970 - Arrays\
чтобы "перебрать" варианты, строка с 1127 - Parameter Expansion\
при написании функций, с 3335 страницы\

# С учётом ответа на предыдущий вопрос, как создать однократным вызовом touch 100000 файлов? Получится ли аналогичным образом создать 300000? Если нет, то почему?
ответ: 100000 - да, touch file{1..100000}.\
300000- нет, $ touch file{1..300000}\
 -bash: /usr/bin/touch: Argument list too long

# В man bash поищите по /\[\[. Что делает конструкция [[ -d /tmp ]]
ответ: [[  ]] - интерпретирует как один элемент с кодом возврата\
[[ -d /tmp ]] - Проверяет, что /tmp существует и это директория\

# Сделайте так, чтобы в выводе команды type -a bash первым стояла запись с нестандартным путем, например bash is ... Используйте знания о просмотре существующих и создании новых переменных окружения, обратите внимание на переменную окружения PATH

bash is /tmp/new_path_directory/bash\
bash is /usr/local/bin/bash\
bash is /bin/bash\
(прочие строки могут отличаться содержимым и порядком) В качестве ответа приведите команды, которые позволили вам добиться указанного вывода или соответствующие скриншоты.
ответ: $ ln -s /usr/bin /tmp/new_path_directory
$ PATH=/tmp/new_path_directory:${PATH}

# Чем отличается планирование команд с помощью batch и at?
ответ:at выполняется строго по расписанию\
batch выполняется, когда позволит нагрузка на систему (load average упадёт ниже 1.5 или значения, заданного командой atd)\
Завершите работу виртуальной машины чтобы не расходовать ресурсы компьютера и/или батарею ноутбука - vagrant suspend.
