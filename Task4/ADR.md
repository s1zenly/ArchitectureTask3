### <a name="_b7urdng99y53"></a>**Название задачи:** 
### <a name="_hjk0fkfyohdk"></a>**Автор:**
### <a name="_uanumrh8zrui"></a>**Дата:**
### <a name="_3bfxc9a45514"></a>**Функциональные требования**
Опишите здесь верхнеуровневые Use Cases. Их нужно оформить в виде таблицы с пошаговым описанием:

|**№**|**Действующие лица или системы**|**Use Case**|**Описание**|**Комментарий**|
| :-: | :- | :- | :- | :- |
| UC1 | Микросервис депозитов,<br> кол-центр,<br> SMTP-шлюз | Отправка/получение ставок депозитов | 1. Кол-центр отправляет mail-сообщение на почту сервиса с нужным пользователем<br> 2. Сервис депозитов читает автоматически сообщения с этого адреса<br> 3. Отправляет данные по пользователю обратно с помощью SMTP на почтовый адрес | Важно добавить валидацию адресов с которых приходят сообщения. В MVP встраиваем логику email-сообщений в сервис депозитов, после можно будет вынести в отдельное место при появлении других сервисов|
| UC2 | Микросервис депозитов,<br> Внешний кол-центр,<br> SMTP-шлюз | Отправка/получение ставок депозитов | 1. Внешний кол-центр отправляет mail-сообщение на почту сервиса с нужным пользователем<br> 2. Сервис депозитов читает автоматически сообщения с этого адреса<br> 3. Отправляет данные по пользователю обратно с помощью SMTP на почтовый адрес | Важно добавить валидацию адресов с которых приходят сообщения. В MVP встраиваем логику email-сообщений в сервис депозитов, после можно будет вынести в отдельное место при появлении других сервисов|

### <a name="_u8xz25hbrgql"></a>**Нефункциональные требования**
Опишите здесь нефункциональные требования и архитектурно значимые требования.

|**№**|**Требование**|**Комментарий**|
| :-: | :- | :- |
|1| Перегрузка кол-центра банка не должна влиять на доступность консультаций| Во избежании таких проблем в прошлом (третьем) задании в архитектуре я уже учел переключение на партнерский сервис кол-центра |
|2| Партнерский кол-центр не имеет возможности делать API-вызовы | При этом они готовы принимать актуальные ставки файлами |
### <a name="_qmphm5d6rvi3"></a>**Решение**

[C4-context-url](https://www.plantuml.com/plantuml/uml/bP9FRzD04CNl-HI3LObK8l654rAbGgYuK8YQvboDrvF6Ol-OdTc6V7jc7JiiH0XnstspxwStpxvbmIZ9sTchpXkRMeAzIC_lwZhYOVdSoJurYIcQu8MyB4rmTM_HPy-2fRLTKw_UBjPPsjv_hXsoK5JfQQKEx3p5PP_vipL53dwUOM-WsWZw5gF01_JVOAjYfQeE6H2QhF5HIQwwdiqsmscUrTFnml_Ljd0QAUMg9JRnfdflBPWKeyO6vRzqXbXn1UqZzO4xKTnukeHyeGEquz2XnsToohi8ztJtG-O6hLtfD98ILQ3eqS9ALJZ94_wwTB7ZHx9amh3M_MOntlxoMFfFA7J0u_3wSRqOhpdB0zcntxAhAuiDsPjgcykLFGt3rrpia7sbe-pcRD-GRncqTOXag7jHM8k24FnKq32TBX1HSjyNy6BVFzYHlYTYnKW0LWLo6uwOjVL1pBln5BXiEmz-qOO_pmYVtiCkn7EeiDjHd5ALIIP2cMTO3vkGvEndGKdyZpI_VQGIMJyGjd3diBFJNbEMilB_1jpgA3dx4m00)<br>
[C4-container-url](http://www.plantuml.com/plantuml/uml/jLPDR-Cs4BthLx360iq2ZNtPNWe4M7-asnQRhXkxw36Wg8dDX29LaeetRVhVEoE9pbWHt6ItkIGYfNdlpUCCn-z3b3xMfSc-qLQPkW2nZR4AFqmcNkx66nstTLu7yChP23QEbIidbP6MOav3B8pE9_DtfqlQ-ltYuwIK8OB7hQivHaXjmOyhmi-o9VZWx0cXVIT6Csbl1JsFS87_2u5IR85gH8wlHc-pR7MFMENLpDMqVtyIlRm3q-vYqBfPYcbLZTwAlxDCY3tboGvotCUF_e0yw0X8yYQ2sjgpqVAdvUGIf8hZcq3R1GJbpqRDLX3HYRW5WS_QsI3STRCadVi5OWiFmTLUWK398e0j0cxzMKDuXC2GE_2O1zTLkbmRQALziWRt11d1v8r_FL-B7xqiOUVyhNWt_fw9N7TQlWsYQjoKfd5BsmrALcXK5DVEYr9QkM6ReT5vNQFEdY2PAvGohQChPTHAp3gqrcMcQm6cskgU5k96BHj0A9GIcg16mIr0HJWUbFD5wvsNDYHZKKyIrvUaf35piD43AflZGhIhfvf-aNVoOLLv8fev5vcw5Rgl5P2MHgLGo5gRA9_oXJ9ya15syXxvLXUhqsx5-3hGgGWCLji8dl91zXqs2kOau3FkqQb4C9XvsLdIOooWSa57f5kqJozARIeix9WITjnK6w95xzBCEF4YVop0nUom1CL2HfdBm5lbOYLMltrarEcRXjMrmQd-2dmdGdHURe2eEIsLMKCudSs7Y3wXZmOESYmILMCjDLI9OCAuZLQf4vC7z5s1UaJbdOAYzX3w2fBdf2AvFgHawKBSUC2qXzLGufHat-skeglAQ2MR4cyzgi3Yf_nC_icolQwhyy-Hwc_TLajNVztgQVsTzwkB5m7TGaH522M483VamY4NworS8TqUaVNP4A4i2erPqID120LK_4_WGnahtalhPMgc8L3-_Y25JZxDWEmIJ3Soqft-niWSp5apDDZ9tGHd7sXuOTXZKAhtPyMrR2natwWfzhAzvDcHjdLFwjEWEAA9GHyqOeB_095WMamgg5HtWO5YRJwivyiECabCUhuI3Xjr8EqrNTqbLRd64xhJHKs3HnSqxBhX-20wRsXBENkjVKdagGMePsL2JbV_e5LC2Fxvkdouu_oUJuW_MnsrDFglfcSRZMcGTtSwvb80xsMMHNx_maEdfFgrHDZ9iAIYxrFYFkxNS8hiMAY_q3Uw8X8ZWauyt40xnlxhlD9l6sKq73qzxDKlRw1mf3lP3VQQTlOkojTaIbRnn1BJ2YprsEElFi-ePI9x4JYcyp_YyuBZS-nuyQNvzDnpFXWhN3lza2_4UIcrIPX3v_T523maEV6SsFVufYxDlm00)<br>

[C4-context-image](С4-context-image.png)<br>
[C4-container-image](C4-container-image.png)<br>

Исходя из имеющегося с прошлого задания нового сервиса депозитов, мы зная контекст ограничений отправки запросов немного меняем архитектуру.
Теперь запросы от кол-центров идут через email взаимодействия с сервисом. Такое решение даст возможность узнавать ставки по каждому пользователю, а не только общие. А кол-во запросов ограничено кол-вом сотрудников в двух кол-центрах, которое мы можем обработать

### <a name="_bjrr7veeh80c"></a>**Альтернативы**
Из альтернативных решений рассматривалось только вынести логику работы с SMTP-сервером в отдельный шлюз для всей системы

**Недостатки, ограничения, риски**
- На этапе MVP написание нового сервиса для одной задачи будет трудоемко и излишне
- Нужно будет поддерживать решение и сразу думать о взаимодействии с потенциальными новыми продуктами

