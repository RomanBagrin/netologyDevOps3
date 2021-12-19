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

Хелп говорит
ulimit [-HSabcdefiklmnpqrstuvxPT [limit]]
              Provides control over the resources available to the shell and to processes started by it, on systems that allow such control.  The -H and -S options specify that the hard   or soft limit is set for the given resource.  <b>A hard limit cannot be increased by a non-root user once it is set </b>; a soft limit may be increased up to the value of the hard     limit.  If neither -H nor -S is specified, both the soft and hard limits are set.  The value of limit can be a number in the unit specified for the resource or one of  the    special  values  hard,  soft,  or  unlimited, which stand for the current hard limit, the current soft limit, and no limit, respectively.  If limit is omitted, the current     value of the soft limit of the resource is printed, unless the -H option is given.  When more than one resource is specified, the limit name and unit  are  printed  before       the value.  Other options are interpreted as follows:
              -a     All current limits are reported
              -b     The maximum socket buffer size
              -c     The maximum size of core files created
              -d     The maximum size of a process's data segment
              -e     The maximum scheduling priority ("nice")
              -f     The maximum size of files written by the shell and its children
              -i     The maximum number of pending signals
              -k     The maximum number of kqueues that may be allocated
              -l     The maximum size that may be locked into memory
              -m     The maximum resident set size (many systems do not honor this limit)
              -n     The maximum number of open file descriptors (most systems do not allow this value to be set)
              -p     The pipe size in 512-byte blocks (this may not be set)
              -q     The maximum number of bytes in POSIX message queues
              -r     The maximum real-time scheduling priority
              -s     The maximum stack size
              -t     The maximum amount of cpu time in seconds
              -u     The maximum number of processes available to a single user
              -v     The maximum amount of virtual memory available to the shell and, on some systems, to its children
              -x     The maximum number of file locks
              -P     The maximum number of pseudoterminals
              -T     The maximum number of threads

              If  limit  is  given, and the -a option is not used, limit is the new value of the specified resource.  If no option is given, then -f is assumed.  Values are in 1024-byte
              increments, except for -t, which is in seconds; -p, which is in units of 512-byte blocks; -P, -T, -b, -k, -n, and -u, which are unscaled values; and, when in  posix  mode,
              -c and -f, which are in 512-byte increments.  The return status is 0 unless an invalid option or argument is supplied, or an error occurs while setting a new limit.


11.  fvgvf




