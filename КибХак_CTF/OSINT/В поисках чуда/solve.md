1. **Получение данных о последнем рейсе:**
   - Задание состоит в сборе данных с последнего рейса: номера рейса, аэропорта вылета и координат (с точностью до 3 знаков). 
    ![aircraft](https://github.com/kedxmi/CTF/assets/149513988/cd87bb0c-2f3d-4c91-b071-0be365319a01)

2. **Поиск информации о самолете:**
   - В браузере мы находим фотографию самолета.
   - По фотографии определяем информацию о самолете: авиакомпанию (US Airways Shuttle) и тип (Airbus A320).

3. **Поиск фотографий с информацией:**
   - Находим в сети сайт, где размещаются фотографии самолетов с подробной информацией о них [JetPhotos](https://www.jetphotos.com/).
   - Используя фильтры, находим наш самолёт и информацию об "аварийной посадке на Гудзоне".

4. **Раскрытие дополнительных данных из Википедии:**
   - Открываем статью в Википедии о "аварийной посадке на Гудзоне".
   - Узнаем недостающую информацию: рейс - AWE1549, аэропорт вылета - Ла-Гуардия (LGA), а также координаты.

5. **Получение флага:**
   - В результате, мы формируем флаг: `kxctf{AWE1549_LGA_40.769_-74.004}`.
