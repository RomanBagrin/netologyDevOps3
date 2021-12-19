# netologyDevOps3
Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"
1. Установил 
2. Установил
3. Подготовил
4. Создал и запустил виртуальную машину
5. Посмотрел. По умолчанию выделено 1024 памяти и 2 ядра.
6. скорректировал конфиг для изменения памяти и ядер:

Vagrant.configure("2") do |config|

 	config.vm.box = "bento/ubuntu-20.04"
	config.vm.provider "virtualbox" do |v|
	v.customize ["modifyvm", :id, "--memory", "2048"]
	v.customize ["modifyvm", :id, "--cpus", "3"]
	end
end
7. Подключился по ssh, попрактиковался
8. для поиска номера строки и имени переменной воспользуемся командой grep:
man bash |grep history -n 
Среди выведенных строк будет следующее:
1886:              value  less  than zero, the number of history entries is not limited.  By default, the number of history entries is set to the value of the HISTSIZE shell variable.
Таким образом, в строке мануала 1886 указано, что в переменной HISTSIZE задается размер журнала команд. 
