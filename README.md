# Скринсейвер Windows 3.11 на Pygame

## Описание
Этот проект почти полностью воссоздает классический скринсейвер Windows 3.11 с использованием Python и Pygame.

## Установка
1) Создание виртуального окружения:
Откройте терминал (или командную строку) и выполните команду:
```python -m venv venv```

2) Активация виртуального окружения:
```source venv/Scripts/activate```

3) Установка зависимостей:
```pip install -r requirements.txt```

(на этом этапе у меня возникла проблема и пришлось устанавливать зависимость вручную для pygame):
```pip install pygame```

4) Импорт библиотек:
   ```import pygame```
   ```import random```

5) Инициализация Pygame
   ```pygame.init()```

6) Установка размеров окна
  ```screen_width = 800```
   ```screen_height = 600```
   ```screen = pygame.display.set_mode((screen_width, screen_height))```

7) Переменная для управления игровым циклом
   ```done = False```

8) Создание списка звезд
   ```stars = []```

9) Функция для создания новой звезды
   ```def new_star():```
    ```x = random.randint(-screen_width // 2, screen_width // 2)```
    ```y = random.randint(-screen_height // 2, screen_height // 2)```
    ```z = random.randint(1, 256)```
    ```return [x, y, z]```

10) Создание звезд
    ```for _ in range(1500):```
    ```stars.append(new_star())```

11) Скорость движения звезд
    ```speed = 0.1```

12) Сам цикл
    ```while not done:```

13) Обработка событий
    ```for event in pygame.event.get():```
        ```if event.type == pygame.QUIT:```
            ```done = True```

14) Очистка экрана
    ```screen.fill((0, 0, 0))```

15) Обновление и отрисовка звезд
        ```for i in range(len(stars)):```
        ```star = stars[i]```
        ```star[2] -= speed```

16) Замена звезды, если она слишком близко
            ```if star[2] <= 0:```
            ```stars[i] = new_star()```
            ```continue```

17) Преобразование 3D координат в 2D
    ```x = int(star[0] * 256 / star[2] + screen_width // 2)```
    ```y = int(star[1] * 256 / star[2] + screen_height // 2)```

18) Изменение цвета звезды
            ```brightness = int(255 * (1 - star[2] / 256))```
        ```if brightness < 128:```
            ```color = (255, brightness * 2, 0)```
        ```else:```
            ```color = (255, 255, (brightness - 128) * 2)```

19) Изменение размера звезды
            ```size = int(3 * (1 - star[2] / 256))```

20) Отрисовка звезды
            ```if 0 <= x < screen_width and 0 <= y < screen_height:```
            ```pygame.draw.circle(screen, color, (x, y), size)```

21) Обновление экрана
        ```pygame.display.flip()```

22) Завершение работы Pygame
    ```pygame.quit()```

## Изменения от себя
Я добавил изменения цвета самих звезд: когда звезды очень далеко - они красные, когда примерно на середине экрана - становятся желтыми, а когда близко к краям - белыми
