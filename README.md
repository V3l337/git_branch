История команд
1. Подготовка репозитория
Клонирование репозитория:
    git clone https://github.com/V3l337/git_branch.git
Создание каталога branching и файлов:
    mkdir branching
    touch branching/merge.sh
    touch branching/rebase.sh
2. Создание коммита
Добавление и коммит файлов с сообщением:
    git add .
    git commit -m "prepare for merge and rebase"
    git push origin main
3. Работа с веткой git-merge
Создание ветки git-merge и внесение изменений в merge.sh:
    git checkout -b git-merge
Первое Изменение merge.sh...
    git commit -a -m "merge: @ instead *"
    git push origin git-merge
Второе изменение и коммит:
    git commit -a -m "merge: use shift"
    git push origin git-merge
4. Работа с веткой git-rebase
Создание ветки git-rebase от старого коммита:
    git checkout -b git-rebase <commit_hash>
Внесение изменений в rebase.sh и коммиты:
    git commit -a -m "git-rebase 1"
    git push origin git-rebase
# Второй коммит
sed -i 's/Parameter: /Next parameter: /' branching/rebase.sh
    git commit -a -m "git-rebase 2"
    git push origin git-rebase
5. Слияние веток
Слияние ветки git-merge в main:
    git checkout main
    git merge git-merge
    git push origin main
Выполнение rebase для ветки git-rebase и разрешение конфликтов:
    git checkout git-rebase
    git rebase -i main
# Разрешение конфликтов
    git rebase --continue
    git push -u origin git-rebase -f
6. Финальное слияние
Слияние ветки git-rebase в main:
    git checkout main
    git merge git-rebase
    git push origin main
