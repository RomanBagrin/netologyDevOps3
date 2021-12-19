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
Ignoreboth - опция, при которой не выводятся команды, начинающиеся с пробела и дублирующиеся команды: 

HISTCONTROL
              A  colon-separated list of values controlling how commands are saved on the history list.  If the list of values includes ignorespace, lines which begin with a space char‐
              acter are not saved in the history list.  A value of ignoredups causes lines matching the previous history entry to not be saved.  A value of ignoreboth is  shorthand  for
              ignorespace  and  ignoredups.  A value of erasedups causes all previous lines matching the current line to be removed from the history list before that line is saved.  Any
              value not in the above list is ignored.  If HISTCONTROL is unset, or does not include a valid value, all lines read by the shell parser are saved on the history list, sub‐
              ject  to the value of HISTIGNORE.  The second and subsequent lines of a multi-line compound command are not tested, and are added to the history regardless of the value of
              HISTCONTROL.
	      
9. оророр	      
