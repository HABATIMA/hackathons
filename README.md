# hackathons

   Как это работает?

Искусственный интеллект, который мы разработали, основан на сверточной нейронной сети, которая способна анализировать и обрабатывать каждый кадр видео с удивительной точностью. Нейронная сеть идентифицирует шумы, размытость, артефакты и другие дефекты в кадрах и применяет специализированные алгоритмы для их устранения.

TASK: Разработать схему улучшения качества видео с целью повышения привлекательности видеохостинга RUTUBE для пользователей.

ДЛЯ ТРЕНИРОВОК ИИ: 
1. В папке "сортировка видео" предоставлен код программы, которая будет сортировать видео по двум разным папкам (делить видео на разрешения 144p и 480p).
2. После сортировки видеоматериала, для обучения нашего ИИ, нам нужно конвертировать видеоматериал в его раскадровку. Для этого запускаем код из папки "сортировка кадров", который автоматически конвертирует видеоматериал в покадровые отдельные изображения. Программа после конвертации видеофайлов выберет случайно 15 любых кадров из каждого видео и отправит их по папкам 'output_144p_frames' и 'output_480p_frames' соответственно.
3. Далее нам требуется запустить и обучить искусственный интеллект.

3.1. Берём программу, код которой хранится в папке "ИИ". Для её обучения нам потребуется указать пути к папкам с хорошими и плохими изображениями (строки 95 и 96), а также нашу предобученную модель (строка 123).

3.2 Вводим параметры для обучения (batch_size= – количество тренировочных объектов. epochs= – количество эпох обучения модели) и запускаем процесс.

ДЛЯ ПРОВЕРКИ ИИ:

После окончания обучения модели, она автоматически сохранится (причём сохранятся и бэкапы эпох тренировок), с её помощью можно обработать загруженный видеофайл, качество которого будет увеличено в зависимости от того, насколько хорошо вы обучили ИИ.

Для этого в папке 'демонстрация' необходимо в 17 строке указать путь к папке с изображениями плохого качества, а в 23 строке загрузить модель.

Запускаем этот файл, результаты работы ИИ будут находиться в папке 'super_res_test_results'


COMMENTS: Для оптимизации работы ИИ и снижения нагрузки на серверы при работе данной модели в компании RUTUBE, стоит после первого улучшения видеофайла при просмотре любым пользователем, сохранить на сервере данные, полученные после обработки, для использования при дальнейших запросах данного видеоматериала, так как при большом потоке пользователей вычислительных мощностей может не хватить для постоянной обработки материала, и могут возникнуть перебои в работе стримингового сервиса или фермы для улучшения видеофайлов.

