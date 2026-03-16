# Инструкция по запуску проекта CarRent

1. Клонируем репозиторий develop:
https://github.com/alexanderradko190/develop.git

2. Клонируем репозиторий car-rent-backend:
https://github.com/alexanderradko190/car-rent-backend.git

Копируем .env.example и создаем .env файл.
Для генерации тестовых данных на русском языке указываем
APP_FAKER_LOCALE=ru_RU

3. Клонируем репозиторий car-rent-helper:
https://github.com/alexanderradko190/car-rent-helper.git

Копируем .env.example и создаем .env файл
Проверяем, что база данных для проекта создана

4. Переходим cd develop и выполняем сборку:
```bash
docker-compose up -d --build
```

5. Переходим cd car-rent-backend.
Генерируем ключ и JWT-секрет:
```bash
docker exec laravel-app php artisan key:generate
docker exec laravel-app php artisan jwt:secret
```

Создаём симлинк для storage:
```bash
docker exec laravel-app php artisan storage:link
```

Накатываем миграции:
```bash
docker exec laravel-app php artisan migrate
```

Раскатываем тестовые данные через Seeder и Faker
```bash
docker exec laravel-app php artisan db:seed
```


6. Клонируем car-rent-frontend
https://github.com/alexanderradko190/car-rent-frontend.git

Переходим cd car-rent-frontend

Выполоняем: 
```bash
npm install
npm run dev
```

Проект запускается на localhost:5173, API проксируется на localhost
