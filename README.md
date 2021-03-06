# GoFinalTest
Выпускное задание:

Программа читает из stdin строки, содержащие URL. На каждый URL нужно отправить HTTP-запрос методом GET
и посчитать кол-во вхождений строки "Go" в теле ответа. В конце работы приложение выводит на экран общее количество найденных строк "Go" во всех переданных URL, например:

$ echo -e 'https://golang.org\nhttps://golang.org' | go run 1.go
Count for https://golang.org: 9
Count for https://golang.org: 9
Total: 18

Каждый URL должен начать обрабатываться сразу после считывания и параллельно со считыванием следующего. URL должны обрабатываться параллельно, но не более k=5 одновременно. Обработчики URL не должны порождать лишних горутин, т.е. если k=5, а обрабатываемых URL-ов всего 2, не должно создаваться 5 горутин.

Нужно обойтись без глобальных переменных и использовать только стандартную библиотеку.

Код необходимо залить в публичный репозиторий github или на gist.

Общие требования:
- При запуске через stdin на вход подаются url, после обработки списка программа завершается
- В случае если в stdin пусто, программа завершается
- Url разделены переносом строки
- Максимальное количество горутин для обработки всего списка 5
- При получении менее 5 url на вход, количество запущеных горутин не должно превышать кол-во url
- Url обрабатываются паралельно
- На каждый url генерируется get запрос в теле ответа которого считается количество вхождений подстроки 'Go'
- После обработки url в stdout выдодится строка с указанием обработанного url и количество найденных вхождений по нему: Count for https://golang.org: 9
- После обработки всех url выводится общее количество найденных вхождений Total: 18
- По всем обработанным url подсчитывается общее количество вхождений
- В случае невалидного url генерируется строка в stderr, количество найденных вхождений возвращается равным 0
- Нужно обойтись без глобальных переменных и использовать только стандартную библиотеку
