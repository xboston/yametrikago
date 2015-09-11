yametrikago
===========

Библиотека работает только с JSON форматом.

Для работы необходим логин с паролем, код или токен (oauth_token).

Необходимые для работы параметры можно получить зарегистрировав приложение вот тут https://oauth.yandex.ru/client/new

Пример использования
--------------------

```

package main

import (
	"fmt"
	"log"

	Metrika "github.com/xboston/yametrikago"
)

func main() {

	log.Println("Start")

	var (
		clientId, clientSecret, username, password, token, code string
		err                                                     error
	)

	//
	clientId = ""
	clientSecret = ""
	username = ""
	password = ""

	//
	code = ""

	// при указании токена остальные параметры не обязательны
	token = ""

	metrika := Metrika.NewMetrika(clientId, clientSecret, username, password, token, code)
	metrika.SetDebug(true)

	err = metrika.Authorize()
	PanicIfErr(err)

	counterList, err := metrika.GetCounterList()
	PanicIfErr(err)

	Debug(counterList)
}
```


Основано на проекте yametrikapy: https://github.com/pikhovkin/yametrikapy/blob/master/yametrikapy/core.py
