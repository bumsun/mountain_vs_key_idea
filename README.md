# Сравнение моделей классификаторов от Mountain Heads и Key Idea (Победители) для классификации отзывов хакатона SBERCODE 2020 года

## Описание задачи
Разработать систему классификации отзывов пользователей в AppStore / Google Play. Нужно учитывать их тональность (баг, дефект, замечание, пожелание), а также уметь отправлять ответственным командам(отделам).
В файле comand_description.txt содержится описание команд(отделов) сбербанка. Необходимио ознакомится с информацией чтобы разобраться, какие отделы за что отвечают т.к. их названия не отражают этого.

## Введение
Команда победителей хакатона Key Idea любезно открыла доступ к своей модели и мы ее протестировали. Проверка происхидла на 20 отзывах. Эти отзывы взяты случайным образом и имеют в себе различные проблемы пользователей. 

Скриншоты теста отзывов команды Key Idea находятся в папке reviews_screenshots_Key_Idea. 
Скриншоты Теста отзывов команды Mountain Heads находятся в аналогичном каталоге с названием reviews_screenshots_Mountain_heads. 
У ребят акцент был на IOS поэтому приставку iOS во всех классах опускаем. Например iOS Platform будет равен просто отделу мобильной разработки. 
Мы перевели информацию из скриншотов в текстовое описание для более удобного сравнения. Сами же скриншоты служат доказательством реальности результатов проверки.

## Как будем сравнивать модели?
Данные изначально не размечены, это мешает автоматизировать проверку качества. 
Чтобы максимально объективно сравнить модели мы будем считать следующим образом:
1) За каждый верно предсказанный класс будем добавлять (+1) бал для модели. Верно предсказанным классом будет считаться тот, который может описать данный отзыв или в случае с отделом, класс может верно определить команду(отдел), которому будет интересен данный отзыв. 
2) За каждый не верно предсказанный класс или отдел будем вычитать (-1) бал у модели.
При такой оценке ложные результаты или непредсказанные будут наказывать модель.
После сравнения всех отзывов сложим полученные балы и та модель, которая работает лучше будет иметь большее количество баллов

> Текст №1: мне нравится,что не выходя из дома можно управлять всеми финансами

* __Mountain Heads__: похвала (+1) = 1. 
* Key Idea: PFM БЮДЖЕТ(-1), CБОЛ Классические переводы(-1), Sberbank ID B2C(-1) = -3

> Текст №2: не сбербанк, а. быстро деньги какие то, вы хоть предупреждайте, что без страховки на кредит проценты как вулкан взрываются, что человек в такой тупик попадает, мало не покажется, вам то кучу документов неси, то ненадо, где логика? и автоответчик ваша тоже без плохих слов не опишешь, а операторы, когда разговор записывается, делает нужные документы, после того как истерику закатил. страховая компания отвратительная, а на автоответчик любой человек может посылать, даже без образования. спасибо

* Mountain Heads: претензия(+1),похвала(-1),вопрос(+1),Цифровой Кредит(+1),Текстовый чат(-1),[ЕФС].Кредитные карты,ЕФС.(+1) Страхование(+1) = 3. 
* Key Idea: Телеком(-1), CБОЛ Классические переводы(-1), Sberbank ID B2C(-1) = -3

> Текст №3: после обноление- цирк какой-то. это финансовое приложение. нафиг мне третьяковка с хабенским, или путешествия по транссибу! пусть 20 ти летние этим развлекаются. мне, шаблоны которые исчезли, куда важнее.подскажите, люди добрые, как откатить назад! п. с. игорь! забыл что аккаунт в гуглее другой=) ответ сбербанку:я попросил помочь откатить, а не советов! ответ 2:не льстите себе сьербанк! вы идете в ногу со временем, ориентируясь на молодых. легче сделать лайт версию.

* Mountain Heads: ЕФС.Автоплатежи (-1) = -1. 
* Key Idea: CБОЛ Классические переводы(-1), Sberbank ID B2C(-1) = -2

> Текст №4: приложение тормозит смс на 900 пришло о том, что было зачисление, в приложении сбербанк онлайн ничего нет, дважды заходил, обновлял, в итоге появились сведения о зачислении, ура)) , что-то не совсем корректно вы обновили, только хуже стало, да и подтверждения в виде смс на 900 хорошо вернуть, а то деньги пришли или нет, надо смотреть в приложении сбербанк онлайн, это не удобно. !!!!

* Mountain Heads: ошибка UX(+1),претензия(+1) = 2. 
* Key Idea: DBP. Витрины продаж(-1), CБОЛ Классические переводы(+1), Sberbank ID B2C(-1) = -1

> Текст №5: почему после обновления у меня программа выдаёт сбой?((((

* Mountain Heads: баг(+1),вопрос(+1),Мобильная разработка(+1) = 3. 
* Key Idea: Развитие лояльности в МП СБОЛ(-1), iOS Platform(+1) = 0

> Текст №6: клёвое приложение, не надо бегать и платить в доли от дома. всё снимается с карты, клас :-):-):-)

* Mountain Heads: похвала(+1) = 1. 
* Key Idea: Sberbank ID B2C(+1), ЕФС. Платежи МП (+1) = 2

> Текст №7: хотелось бы чтоб приложение оставалось работать после того как закончился интернет , чтоб можно было оплатить онлайн интернет.

* Mountain Heads: претензия(-1),фича(+1),ЕФС.Платежи МП(+1),Платежи. Штрафы(+1) = 2. 
* Key Idea: Sberbank ID B2C(+1), CБОЛ Классические переводы(-1) = 0

> Текст №8: сбербанк рау в крыму не работает санкции,плохо очень

* Mountain Heads: баг(+1),Мобильная разработка(+1) = 2. 
* Key Idea: Телеком(-1), Текстовый чат(-1), CБОЛ Классические переводы(-1) = -3

> Текст №9: действительно, приложение очень удобное, но иногда случаются сбои ( редко). написал обращение в сб сбербанка по поводу "фишинга" - ни ответа, ни привета! хотелось, чтобы хотя бы информировали и давали рекомендации. берите пример с google (google - аккаунт, google - ассистент). в приложении нет информации о страховании вкладов и банковских карт. а было бы неплохо! чтобы вовремя продлять, и страховщикам доход! почему-то перестали инфомировать о доставке и замены банковских карт, включая кредитные.

* Mountain Heads: претензия(+1),похвала(+1),фича(+1),вопрос(-1),Цифровой Кредит(+1),ВС.МП вклады(+1),[ЕФС].Кредитные карты(+1),ЕФС. Страхование(+1) = 6. 
* Key Idea: DBP. Витрины продаж(-1), CБОЛ Классические переводы(-1), Sberbank ID B2C(-1) = -3

> Текст №10: приложение удобное жаль что нельзя настроить ежедневные автоплатежи. было бы удобно, чтобы каждый день ребенку для школы скидывалась

* Mountain Heads: претензия(+1),похвала,фича(+1),Платежи. Штрафы(-1),ЕФС.Автоплатежи(+1) = 2. 
* Key Idea: ЕФС.Автоплатежи(+1), Развитие лояльности в МП СБОЛ(-1), iOS Platform(+1), Sberbank ID B2C(-1) = 0

> Текст №11: я не пойму, почему не удаляются уведомления, нет возможности, ввести одноразовый код, для оплаты?!

* Mountain Heads: вопрос(+1),PUSH уведомления(+1),Платежи. Штрафы(+1) = 3. 
* Key Idea: PUSH IOS(+1), IOS Platform(+1), Sberbank ID B2C(+1) = 3

> Текст №12: на днях скачал, установил. пока всё нравится, программа понятна и удобна, хотя пользуюсь ею лишь в крайних случаях из-за мелкости смартфоно-экрана, на коем в принципе неудобно что-либо делать.

* Mountain Heads: ошибка UX(+1),похвала(+1),Глобальная навигация(+1) = 3. 
* Key Idea: Развитие лояльности в МП СБОЛ(-1),CБОЛ Классические переводы(-1),Sberbank ID B2C(-1) = -3

> Текст №13: очень быстро и просто проводить оплату.

* Mountain Heads: похвала(+1),Платежи. Штрафы(+1) = 2. 
* Key Idea: ЕФС.Автоплатежи(-1),CБОЛ Классические переводы(-1),Sberbank ID B2C(+1) = -1

> Текст №14: когда включается защита телефон начинает лагать, очень раздражает. дополню отзыв: проверка длится 1-2минуты, иногда перезагружается телефон, приложения вылетают.

* Mountain Heads: баг(+1),ошибка UX(-1),похвала(-1),Мобильная разработка(+1) = 0. 
* Key Idea: IOS Platform(+1), Sberbank ID B2C(-1) = 0

> Текст №15: точно не могу сказать с какого момента, вероятно после последнего обновления... при попытке открыть карту происходит сброс на страницу ввода пинкода в приложение. при входе в счет, кредит и другие разделы все нормально. сброс только при входе к какую либо из карт. ранее такого не было. кэш чистил, приложение переустанавливал. не помогает! аппарат samsung galaxy a8+ 2018. помогайте срочно!

* Mountain Heads: баг(+1),ошибка UX(-1),претензия(-1),похвала(-1),Мобильная разработка(+1),Глобальная навигация(-1),Digital PIN(+1),Цифровой Кредит(-1),[ЕФС].Кредитные карты(-1) = -3. 
* Key Idea: IOS Platform(+1), Sberbank ID B2C(-1) = 0

> Текст №16: мне все нравится. однако сегодня при пользовании электронной картой digital visa обнаружил, что она не показывает текстовые сообщения тех, от кого переведены деньги. организую юбилей предприятия, и неудобно работать с такими noname переводами.

* Mountain Heads: ошибка UX(+1),похвала(+1),СБОЛ. Классические переводы(+1) = 3. 
* Key Idea: CБОЛ Классические переводы(+1),Sberbank ID B2C(-1) = 0

> Текст №17: после обновления ужасно!!!!! раньше всё было ясно и понятно, сейчас навертели квадратиков, дольше ковыряешься, чтобы что-то найти...отвратительно....

* Mountain Heads: претензия(+1) = 1. 
* Key Idea: iOS Realease Engineer(-1), Краудфандинг(-1), IOS Platform(-1), Sberbank ID B2C(-1) = -4

> Текст №18: почему нет в сбп кредит европа банка?

* Mountain Heads: вопрос(+1),Цифровой Кредит(+1),[ЕФС].Кредитные карты(+1) = 3. 
* Key Idea: Телеком(-1), CБОЛ Классические переводы(-1) = -2

> Текст №19: плохо прослеживается динамика расходов и зачислений ден. средств
* Mountain Heads: баг(-1),Мобильная разработка(-1) = -2. 
* Key Idea: PFM Бюджет(+1),Sberbank ID B2C(-1) = 0

> Текст №20: мне интересно, зачем в приложении услуга - "связь с банком", если с другой стороны робот или бестолковый консультант, которые не могут ничем помочь, а по телефону нервный оператор? ничего не меняется..

* Mountain Heads: ошибка UX(-1),претензия(+1),вопрос(+1),Текстовый чат(1) = 2. 
* Key Idea: Текстовый чат(+1), CБОЛ Классические переводы(-1), Sberbank ID B2C(-1) = -1

## Подведение итогов
* Mountain Heads = 33 балла. 
* Key Idea = -21 балл

Результаты показывают, что решение Key Idea на некоторых отдельных отзывах проявило себя лучше, но по общей картине решение команды Mountain Heads смогло значительно лучше промаркировать данную выборку отзывов.  
Так же анализ показал, что решение Key Idea игнорировало тональность и предсказывало только отделы, что так же сыграло роль в столь сильной разнице.
