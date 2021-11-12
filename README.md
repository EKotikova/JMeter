#  JMeter

Учебный скрипт по JMetr
В данном проекте представлен учебный скрипт, 
выполненный в с помощью  JMetr.

Требования к запуску скрипта на локальном компьютере: OC Windows(x64), 
OpenServer_5_7_6 c настройками (Apache_2.4PHP_7.2; PHP_7.3, MySQL-5.6),
testlink 1.9.0 - приложение на основе,которого построен сценарий выполнения скрипта в JMeter.
jre 1.8.0 или jdk-17_windows-x64_bin
apache-jmeter-5.4.1


Установите и настройте OpenServer  на своей локальной машине. 
Далее распакойте testlink в папку OpenSever\domains. Перезапустите OpenServer и в браузере наберите "testlink\".
При первом запуске testlink у Вас откроеся страница установки. Выполните установку testlink согласно иструкции.
Установите на компуютер виртуальную машину java и распокуйте архив apache-jmeter в любой папке на вашей локальной машине.
Скачайте файл с расширением .jmx с данного репозитория и откройте с помощью ApacheJMeter, находящегося в папке apache-jmeter\bin.
Установите на компуютер виртуальную машину java и распокуйте архив apache-jmeter в любой папке на вашей локальной машине.
![apache_jmeter](https://user-images.githubusercontent.com/14973822/141525271-6036e36b-693f-441b-b990-25a044213530.PNG)
По следующему сценарию в testlink:

# 0. Открыть главную страницу в системе
Get http://testlink/login.php

# 1. Зайти в систему

Post http://testlink/login.php
reqURI: 
destination: 
tl_login: User1
tl_password: USER1
login_submit: Войти
Get http://testlink/index.php

Get http://testlink/lib/general/navBar.php
Get http://testlink/lib/general/mainPage.php


# 2.Кликнуть на кнопку [Test specification]


Get http://testlink/lib/general/frmWorkArea.php?feature=editTc
Get http://testlink/lib/general/staticPage.php?key=editTc
Get http://testlink/lib/testcases/listTestCases.php?feature=edit_tc


# 3.Кликнуть на [Suit 1]


Get http://testlink/lib/testcases/archiveData.php?print_scope=test_specification&edit=testsuite&level=testsuite&id=3&form_token=1933091267&


# 4. Кликнуть на  кнопку [Create]


Post http://testlink/lib/testcases/tcEdit.php
containerID: 3
create_tc: Создать тест

Get http://testlink/third_party/fckeditor/editor/fckeditor.html?InstanceName=summary&Toolbar=tl_default
InstanceName: summary
Toolbar: tl_default

Get http://testlink/third_party/fckeditor/editor/fckeditor.html?InstanceName=preconditions&Toolbar=tl_default
InstanceName: preconditions
Toolbar: tl_default

# 5. Заполнить  все поля тест-кейса и кликнуть на кнопку  [Create]


Post http://testlink/lib/testcases/tcEdit.php?containerID=3

testcase_id: 0
testsuite_id: 3
do_create: do_create
do_create_button: Создать
testcase_name: Title
summary: <p>&nbsp;Summary</p>
preconditions: <p>&nbsp;repcondions</p>
ot_removedLeft: 
ot_removedRight: 
ot_addedLeft: 
ot_addedRight: 
ot_newLeft: 
ot_newRight: 
do_create: do_create

# 6.Найти в дереве и кликнуть на название тест-кейса

Get http://testlink/lib/testcases/archiveData.php?
version_id=undefined&edit=testcase&id=9&form_token=2123080428

version_id: undefined
edit: testcase
id: 9
form_token: 2123080428


# 7.Заполнить поля и кликнуть кнопку [Save]


Post http://testlink/lib/testcases/tcEdit.php

testcase_id: 9
tcversion_id: 10
doAction: doCreateStep
show_mode: show
step_id: -1
step_number: 1
goback_url: http://testlink/lib/testcases/archiveData.php?tcase_id=9&show_mode=show
steps: <p>&nbsp;1.Шаг1</p>
<p>&nbsp;</p>
expected_results: <p>&nbsp;Create step 1</p>


Get http://testlink/third_party/fckeditor/editor/
fckeditor.html?InstanceName=steps&Toolbar=tl_default

InstanceName: steps
Toolbar: tl_default

Get http://testlink/third_party/fckeditor/editor/
fckeditor.html?InstanceName=expected_results&Toolbar=tl_default
InstanceName: expected_results
Toolbar: tl_default

# 8. Удалить нужный тест-кейс

Post http://testlink/lib/testcases/tcEdit.php

testcase_id: 9
tcversion_id: 10
has_been_executed: 0
doAction: 
show_mode: show
delete_tc: Удалить

----------------------------------------------
Post http://testlink/lib/testcases/
tcEdit.php?testcase_id=9&tcversion_id=0
Qury string 
testcase_id: 9
tcversion_id: 0

do_delete: Да, удалить тест!

----------------------------------------------------------
Post http://testlink/lib/testcases/
listTestCases.php?feature=edit_tc
form_token: 2123080428
feature: edit_tc
tpn_view_status: 0
hidden_setting_refresh_tree_on_action: 1
setting_refresh_tree_on_action: on
filter_tc_id: 1-
filter_testcase_name: 
filter_toplevel_testsuite: 0
filter_execution_type: 0

# 9. Кликнуть Logut
--------------------------------
Get http://testlink/logout.php

Get http://testlink/login.php
