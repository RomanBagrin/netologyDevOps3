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
	      
9. Фигурные скобки используются при групповых командах. В скобках перечисляются значения, которые будут применены последовательно для каждой из выполенных команд. Об этом говорится в строке 212:

{ list; }
              list  is  simply  executed in the current shell environment.  list must be terminated with a newline or semicolon.  This is known as a group command.  The return status is
              the exit status of list.  Note that unlike the metacharacters ( and ), { and } are reserved words and must occur where a reserved  word  is  permitted  to  be  recognized.
              Since they do not cause a word break, they must be separated from list by whitespace or another shell metacharacter.

10. Создать 100000 файлов: 

ulimit -s 105000  
touch file{1..100000}.txt

300000 файлов создать не получается, выдается сообщение "ulimit: stack size: cannot modify limit: Operation not permitted". 

Хелп говорит, что нужны рутовые права для изменения жесткого лимита:

ulimit [-HSabcdefiklmnpqrstuvxPT [limit]]
              Provides control over the resources available to the shell and to processes started by it, on systems that allow such control.  The -H and -S options specify that the hard   or soft limit is set for the given resource.  <b> A hard limit cannot be increased by a non-root user once it is set </b>; a soft limit may be increased up to the value of the hard     limit.  If neither -H nor -S is specified, both the soft and hard limits are set.  

11.  Проверка условия.
-d file      True if file exists and is a directory.

12. Создал соответствующие подкаталоги, куда скопировал bash. Потом в начало $PATH добавил в нужном порядке подкаталоги:

export PATH=/tmp/new_path_directory:/usr/local/bin/:/bin:$PATH

В результате type -a bash вывела строки в нужном порядке.


13. batch — для планировнаия выполнения задачи, когда загрузка системы меньше 0,8. at - планирование выполнения задачи в определенное время.

14. остановил через vagrant halt

