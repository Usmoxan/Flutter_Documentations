# Flutter Named Routes

Flutter-da nomlangan marshrutlar an'anaviy navigatsiya to'plamidan foydalanish o'rniga unga noyob nom berish orqali ma'lum bir ekranga o'tish usulidir. Ushbu yondashuv navigatsiyani yanada o'qilishi, kengaytirilishi va xizmat ko'rsatishini ta'minlaydi. Ushbu postda biz Flutter-da nomlangan marshrutlarni qanday amalga oshirish va marshrutlar o'rtasida ma'lumotlarni uzatishni ko'rib chiqamiz.

## Nomlangan marshrutlarni sozlash


Nomlangan marshrutlarni oʻrnatish uchun avval ularni `MaterialApp` vidjetida `routes` parametri yordamida aniqlashimiz kerak. Mana bir misol:

```dart
MaterialApp(
  title: 'My App',
  routes: {
    '/': (context) => HomeScreen(),
    '/details': (context) => DetailScreen(),
  },
);`
``` 

Ushbu misolda biz ikkita nomlangan marshrutni aniqladik: `'/'` va `/details'`. Foydalanuvchi `/` ga o'tganda, `HomeScreen` vidjeti ko'rsatiladi va `/details` ga o'tganda `DetailScreen` vidjeti ko'rsatiladi.

## Nomlangan marshrutga navigatsiya

Nomlangan marshrutga oʻtish uchun biz `Navigator.pushNamed()` usulidan foydalanamiz. Mana bir misol:

```dart
`Navigator.pushNamed(context, '/details');
``` 

Ushbu misolda biz `/details` nomli marshrutga o'tmoqdamiz. Shuningdek, biz `arguments` parametri yordamida ma'lumotlarni nomlangan marshrutga o'tkazishimiz mumkin:
```dart
`Navigator.pushNamed(
  context, 
  '/details', 
  arguments: {'name': 'Usmoxan', 'age': 20},
);
```

## Nomlangan marshrutdan ma'lumotlarni qabul qilish



Nomlangan marshrutdan ma'lumotlarni olish uchun biz marshrut sozlamalariga kirish uchun `ModalRoute.of()` usulidan foydalanamiz. Mana bir misol:

```dart
class DetailScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final args = ModalRoute.of(context)!.settings.arguments as Map<String, dynamic>;
    final name = args['name'];
    final age = args['age'];
    
    return Scaffold(
      appBar: AppBar(title: Text('Detail Screen')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('Ism: $name'),
            Text('Yosh: $age'),
          ],
        ),
      ),
    );
  }
}
```


Ushbu misolda biz `'/details'` nomli marshrutga uzatilgan `arguments` parametriga kiramiz va ularni `DetailScreen` vidjetida ko'rsatish uchun `name` va `age` qiymatlarini chiqaramiz.

## Hulosa

Nomlangan marshrutlar Flutter ilovasidagi ekranlar orasida harakatlanishning yanada tartibli va kengaytiriladigan usulini taqdim etadi. Ularni `MaterialApp` vidjetida belgilash orqali biz `Navigator.pushNamed()` usuli yordamida ularga osongina o‘tishimiz va `arguments` parametri yordamida ma’lumotlarni uzatishimiz mumkin. Belgilangan ekranda ma'lumotlarni olish uchun biz marshrut sozlamalariga kirish uchun `ModalRoute.of()` usulidan foydalanamiz.
