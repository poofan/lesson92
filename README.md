# Инструкция по запуску приложения ToDoListServlets
## 1. Предварительные требования
Перед запуском убедитесь, что на вашем компьютере установлено следующее:

1. **Java** Development Kit (JDK) версии 17 или выше:
Скачайте и установите с официального сайта **Oracle** или **AdoptOpenJDK**.
- Убедитесь, что **переменная среды** JAVA_HOME настроена.
- Проверьте **версию** Java:
``bash
java -version
``
2. **Apache Tomcat** версии 9 или выше:
a) Скачайте Tomcat с официального сайта.
b) Разархивируйте в удобное место, например: C:\Tomcat (Windows) или /opt/tomcat (Linux).
v) Проверьте запуск Tomcat, перейдя в http://localhost:8080.
3. **Maven**:
Убедитесь, что Maven установлен:
``bash
mvn -version
``
Если Maven не установлен, скачайте его с официального сайта.
## 2. Сборка проекта
Соберите проект с помощью Maven:

``bash
mvn clean package
``
В результате сборки в папке target будет создан файл WAR:

target/ToDoListServlets.war

## 3. Деплой на Apache Tomcat
Скопируйте файл ToDoListServlets.war в папку webapps вашего Tomcat.

Пример (Windows):
``bash
copy target\ToDoListServlets.war C:\Tomcat\webapps\
``
Пример (Linux):
``bash
cp target/ToDoListServlets.war /opt/tomcat/webapps/
``
**Перезапустите Tomcat:**

Windows:
``bash
C:\Tomcat\bin\startup.bat
``
Linux:
``bash
/opt/tomcat/bin/startup.sh
``
Проверьте развертывание, открыв в браузере:

``arduino
http://localhost:8080/ToDoListServlets
``
## 4. Тестирование API
Используйте инструмент, например, Postman, или curl для тестирования API.

### 4.1 Добавление задачи (POST /task)
URL: http://localhost:8080/ToDoListServlets/task
Запрос (Body):
``json
{
  "owner": "Nikita",
  "description": "Wash the dishes today"
}
``
Ответ:
``json
{
  "id": "8df48b8c-c960-41eb-8c97-43e88b055cf6",
  "owner": "Nikita",
  "description": "Wash the dishes today"
}
``
### 4.2 Получение задачи по ID (GET /task)
URL: http://localhost:8080/ToDoListServlets/task?id=<id>
Ответ:
``json
{
  "id": "8df48b8c-c960-41eb-8c97-43e88b055cf6",
  "owner": "Nikita",
  "description": "Wash the dishes today"
}
``
### 4.3 Удаление задачи по ID (DELETE /task)
URL: http://localhost:8080/ToDoListServlets/task?id=<id>
Ответ:
``json
{
  "id": "8df48b8c-c960-41eb-8c97-43e88b055cf6",
  "owner": "Nikita",
  "description": "Wash the dishes today"
}
``
## 5. Решение возможных проблем
### Tomcat не запускается:

1) Проверьте, что порт 8080 не занят другим приложением. Измените порт в файле conf/server.xml (например, на 8081).
2) Убедитесь, что переменная среды JAVA_HOME настроена.
### WAR-файл не разворачивается:

1) Проверьте логи Tomcat в папке logs.
2) Убедитесь, что структура проекта соответствует требованиям Maven.
### Ошибка 404 при обращении к сервлету:

Убедитесь, что вы обращаетесь по правильному пути: http://localhost:8080/ToDoListServlets/task.
## 6. Дополнительные команды
Для перезапуска Tomcat:
``bash
shutdown.sh && startup.sh
``
Для пересборки проекта:
``bash
mvn clean package
``
Теперь ваше приложение готово к использованию!
