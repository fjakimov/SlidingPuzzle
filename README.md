# SlidingPuzzle
Sliding puzzle with 3 levels

1.Опис на апликацијата што ја развив е Sliding Puzzle, која има 3 нивоа Easy(Сложувалка 3x3), Medium(Сложувалка 4x4) и Impossible(Сложувалка 5x5) за апликацијата да биде поинтересна за играње овозможено е избор на слика за сложување по избор.
Линк кон постоечката апликација која се обидував да ја имплементирам:https://slidingtiles.com/en

2.Упатство за користење

При стартување на апликацијата на почетниот прозорец ќе ви биде побарано да изберете тежина на која сакате да ја играте играта
![Home](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/f3aad6d2-5771-4248-8dfa-7d3e10926bfb)
- Easy
  
  ![Easy](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/5392cfa7-2f26-4e57-91f5-46bab1be8d20)
- Medium
  
  ![Medium](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/71f0d9a6-41e5-4c7f-a99d-c98b43746d33)
- Impossible
  
  ![Impossible](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/7ff427db-429a-46c7-ba64-2ff40864da5e)

Правилата за игра се едноставни имате едно жолто квадратче кое се поместува со кликање на неговите соседи.Соседи на жолтото квадратче се сметаат само квадратчињата позади, пред, под и над него.Дијагоналните квадратчиња не се сметаат за соседи и истите неможе да ги поместувате.

3.Опис на решение на проблем

3.1 Победа на корисникот
 
Чувам две листи за следење на локацијата на квадратчето и крајната локација, и посебни променливи win_position и current position од тип стринг.Така следам дали корисникот ја решил слагалката а тоа е методот CheckGame().
![CheckGameMethod](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/dec9671c-af9b-4f1b-8621-26d993e22b64)


3.2 Креирање на формата на слагалката

Чувам листа од PictureBox како и листа од битмапи во која ги додавам соодветно креираните picture boxes и сецканите слики за да бидат соодветни за димензиите на сложувалката.
Исто така чувам уште еден објект од Битмап кој ми ја претставува целосната слика.
Следните објаснувања ќе се однесуваат за Easy класата останатите класи се скоро исти со минијатурни промени во пикселите.
За да го креирам grid-от на играта користам 4 функции:
1.CreatePictureBoxes()
- Методот за креирање на picture boxes.
![PictureBoxes](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/6f5d86e7-7e19-4311-a4f4-cf1afd9f7d38)

2.CropImage(Bitmap main_bitmap, int height, int width)
- За сечкање на сликата се користи следниот метод каде овозможувам сечкање на сликата главна команда тука е cropped_image.SetPixel(i, j, main_bitmap.GetPixel((i + x), (j + y)))
методот ги зима i и j координатите и ја зима бојата на целосната слика, ова го повторува за секој пиксел(ја копира бојата на позицијата од главната слика над исечканите делчиња во листата.
![CroppingImages](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/d2e8e590-763d-4cff-95fd-1223464367a3)

3. PlacePictureBoxesToForm()
- Oвој метод ги распоредува обоените полиња да бидат претставени во формата распоредени на случаен начин.
  ![PlacePictureBoxes](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/42db901d-a954-400c-b8db-d14262b7ce75)
  
4. AddImages()
- Методот AddImages() претставува главниот метод за додавање на сликичките во GroupBox-от.Ја земам сликата Bitmap tempBitmap = new Bitmap(MainBitmap, new Size(390, 390));
со големина 390x390 и го повикувам методот CropImage каде што ја сечкам сликата и со помош на for циклус ги распоредувам на елементите од picture box листата.И на крај ја ставам и целосната слика како позадина во друг GroupBox за корисникот да може да ја гледа истата додека решава.
![AddImages](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/dc92f29d-7bd5-4e50-8c16-ab2104408f7c)

3.3 File->Open, File->New, File->Save

Апликацијата и е овозможено за почнување од ново при кликање на File->New.Со сериализација се обидував да ја зачувам играта но добивав еxception при конверзија на json стринг така да сеуште неможе да се зачува прогресот но во наредниот update сигурен сум проблемот ќе биде решен. За таа потреба чувам и класа наречена ProcessData каде што го update-ирам моменталниот прогрес.

1.File->Open

![FileOpen](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/3c36f595-4390-407e-896a-27519cbb75db)

2.File->New

![FileNew](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/2dd060ca-50a4-4c9b-8ca0-833dbd951937)

3.File->Save

![FileSave](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/0275779b-c0aa-4bf2-949f-0a307f400841)

Класата ProcessData

![ProcesData](https://github.com/fjakimov/SlidingPuzzle/assets/125222930/b970f043-b3af-43f0-baae-dd2e7df6c1c1)










