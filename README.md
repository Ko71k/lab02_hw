>1.Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com.

Создал репозиторий lab02_hw

>2.Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдущем шаге.

    vim README.md
    git add README.md
    git commit -m"Start doing DZ"
    git push origin master
    
>3.Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.

vim howdy_world.cpp
```
#include 
using namespace std;
int main ()
{
cout << "Hello world\n";
}
```

>4.Добавьте этот файл в локальную копию репозитория.

git add howdy_world.cpp

>5.3акоммитьте изменения с осмысленным сообщением.

git commit -m"adeed hw"

>6.Измените исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
vim howdy_world.cpp
```
#include <iostream>
    using namespace std;
    int main (){
        string name;
        cin >> name;
        cout << "Hello world from " << name << "\n";
    }
```

>7.Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
 git commit -m"upgrade hw" -a
 [master b3170da] upgraded hw
 1 file changed, 7 insertions(+), 3 deletions(-)

 Потому что он уже был добавлен на 4 шаге, а коммитить нужно с -a

>8.Запуште изменения в удалёный репозиторий.

git push origin master

>9.Проверьте, что история коммитов доступна в удалёный репозитории.

git log
commit b3170dad3bd1affd2230e010ff0721a21b468f6d (HEAD -> master, origin/master)
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 14:58:58 2021 +0300

    upgraded hw
commit eae0729a837d64f200f2078f8b00f96a201c4a47
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 14:53:36 2021 +0300

    adeed hw

commit c47bbc982716a91d0c3ed5f01b545542f434a002
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 14:26:25 2021 +0300

    added README.md

Часть 2.
>1.В локальной копии репозитория создайте локальную ветку patch1.

git branch patch1
git checkout patch1 
Switched to branch 'patch1'

>2.Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.

vim howdy_world.cpp 
 ```
 #include <iostream>
void main()
{
	std::string name;
	cout >> "Enter name:";
	std::cin << name;
	std::cout >> "howdy world from "<< name;

}
 ```
 
>3.commit, push локальную ветку в удалённый репозиторий.

git commit -m"promoted hw2" -a
[patch1 212c0f3] promoted hw2
 1 file changed, 4 insertions(+), 4 deletions(-)

git push origin patch1
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 388 bytes | 388.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)

>4.Проверьте, что ветка patch1 доступна в удалённом репозитории.
Доступна.

>5.Создайте pull-request patch1 -> master.

На сайте гитхаба

>6.В локальной копии в ветке patch1 добавьте в исходный код комментарии.

vim howdy_world.cpp
```

```
git commit -m"+comment" -a

>7.commit, push.

git commit -m"added comment" -a
git push origin patch1 <<<<<<< HEAD

>8.Проверьте, что новые изменения есть в созданном на шаге 5 pull-request

[patch1 685d391] +comment
 1 file changed, 1 insertion(+)


>9.В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.

Pull request successfully merged and closed
You’re all set—the patch1 branch can be safely deleted.

>10.Локально выполните pull.

git pull origin master

>11.С помощью команды git log просмотрите историю в локальной версии ветки master.

git log
commit 685d39172bd0e5e4eb802f333dda2bf5cf9b5a3c (HEAD -> patch1, origin/patch1)
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 15:04:16 2021 +0300

    +comment

commit 212c0f3c1e2732544434b95d3ce45fc1a8787bac
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 15:02:43 2021 +0300

    promoted hw2

commit b3170dad3bd1affd2230e010ff0721a21b468f6d (origin/master, master)
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 14:58:58 2021 +0300

    upgraded hw

commit eae0729a837d64f200f2078f8b00f96a201c4a47
Author: Ko71k <rassmagin.wolf@mail.ru>
Date:   Mon May 24 14:53:36 2021 +0300

    adeed hw

>12.Удалите локальную ветку patch1.
  
  it branch -D patch1
Deleted branch patch1 (was 685d391).

Часть 3.
>1.Создайте новую локальную ветку patch2.

git branch patch2
git checkout patch2
>2.Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.

clang-format -style=Mozilla howdy_world.cpp 

>3.commit, push, создайте pull-request patch2 -> master.

git commit -m"style=Mozilla" -a
git push origin patch2

>4.В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

Поменял на
//ничего не делает

>5.Убедитесь, что в pull-request появились конфликтны.

CONFLICT (content): Merge conflict in howdy_world.cpp

>6.Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.

git checkout master
git rebase master
git checkout patch2
git merge patch2

>7.Сделайте force push в ветку patch2

git push --force origin patch2

>8.Убедитель, что в pull-request пропали конфликтны.

git add howdy_world.cpp

>9.Вмержите pull-request patch2 -> master.

git commit -m"commit"
