== README
Разработка блога на Ruby on rails

Установка интерпретатора ruby
sudo apt-get install ruby

Скрипт hello_world.rb
puts "Hello, world!"

Выполнение этой команды в irb приводит к тому самому
$ irb
1.9.3-p551 :001 > puts "Hello, world!"
Hello, world!
 => nil 


Пошаговая инструкция по установке Rails на Ubuntu 12.04 LTS
Информация с http://myubuntu.ru/rukovodstvo/kak-ustanovit-ruby-on-rails-na-ubuntu-12-04-lts
Просто следуйте этим простым шагам, и уже через несколько минут вы будете создавать отличные приложения, используя Rails.
Шаг 1.  Установка git и cURL
Для начала, обновите информацию о пакетах на вашем компьютере.
sudo apt-get update
git - простая, быстрая и эффективная система контроля версий. Она легко осваивается, так что даже если у вас нет никакого опыта с Git, вы можете попробовать его в вашем rails-проекте (или любом другом). Вы полюбите его.
sudo apt-get install git
Curl - простая консольная утилита для загрузки файлов из сети, основанная на libcurl. Чтобы установить curl, просто выполните:
sudo apt-get install curl
Шаг 2. Установка RVM и зависимостей
RVM необязателен для установки, но делает управление ruby намного проще. Вы можете попробовать различные реализации ruby, различные версии ruby и без головной боли:
curl -L get.rvm.io | bash -s stable
Теперь вам нужно загрузить RVM
source ~/.rvm/scripts/rvm
Теперь установите необходимые зависимости для RVM:
sudo apt-get -y install build-essential openssl libreadline6 libreadline6-dev zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion
Установка Javascript-машины
В новых версиях Rails вам также требуется Javascript-машина. Установите nodejs -
sudo apt-get install nodejs
Шаг 3. Установите Ruby
Теперь у вас работает RVM, установка и выполнение различных или только одной версии Ruby очень простое. Чтобы установить Ruby, просто введите номер версии в команду установки rvm (или любую другую реализацию ruby, если вы хотите; RVM также поддерживает rbx, ree, JRuby, IronRuby кроме стандартной MRI) -
rvm install 1.9.3
Затем выберите версию Ruby, которую вы хотите использовать
rvm use 1.9.3 --default
Теперь вы можете проверить версию ruby, которая выполняется у вас сейчас:
ruby -v
Шаг 4. Установка Rails
RVM устанавливает ruby, а также утилиту gem (управление библиотеками ruby). Чтобы установить rails, просто используйте gem. Он автоматически установит самую свежую версию, если вы явно не укажете установку более старой.
gem install rails

Далее шла разработка собственно самого блога
http://guides.rubyonrails.org/getting_started.html
http://rusrails.ru/getting-started-with-rails

Далее делались ЧПУ-ссылки для блога.
При этом использовался gem friendly_id.
Для этого нужно сделать пару шагов.

Дописываем в GemFile, который лежит в корне нашего блога строку
gem 'friendly_id'

Сохранаяем. В терминале пишем
bundle  install

Потом открываем файл app/models/article.rb и дописываем туда 2 строки
  extend FriendlyId
  friendly_id :title

Затем во всех контроллерах, где встречается строка
    @article = Article.find(params[:id])

меняем ее на строку 
    @article = Article.friendly.find(params[:id])

(вот на этом моменте было потрачено очень много времени и сил, ответ был тут http://stackoverflow.com/questions/18591501/friendly-id-active-record-not-found)


После чего блог был залит на github, находится по ссылке 
https://github.com/iamsimakov/blog_ruby_on_rails

Чтобы залить блог на github использовались команды из терминала компьютера из папки, где лежит сам блог:
git init
git add
git commit -m «gotovii blog»
git remote add origin https://github.com/iamsimakov/blog_ruby_on_rails.git
git push -u origin master
