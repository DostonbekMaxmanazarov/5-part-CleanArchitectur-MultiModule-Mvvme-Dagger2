# 5-part-CleanArchitecture-MultiModule-Mvvm-Dagger2
> Project: This project is simply a user authorization project". Contained: Recommended app architecture, MultiModule, Mvvm, Dagger2(Dependency Injection).

<img width="360" height="520" hspace="20" alt="Screen Shot 2023-05-02 at 15 02 13" src="https://user-images.githubusercontent.com/77477995/235638281-48b4323e-e382-4939-825a-b3659a07428b.png"> <img width="360" height="520" hspace="20" alt="Screen Shot 2023-05-14 at 21 34 15" src="https://github.com/DostonbekMaxmanazarov/4-part-CleanArchitecture-MultiModule-Mvvm-Koin/assets/77477995/b1df93ed-88d7-49c3-a495-347a14a57726">

[Dagger 2](https://developer.android.com/training/dependency-injection/dagger-basics) - bu Java va Android uchun mashhur dependency injection frameworkidir. Bu bizning ilovangizdagi dependencylarni boshqarishga yordam beradigan, compile time dependency injection frameworki. Dependency Injection - bu ob'ektlarga o'zlarining dependencylarini bevosita qo'lda yaratmasdan dependencylarni tashqaridan  ob'ektlarga taqdim etadi("injected"). Ushbu yondashuv bir xil dependencylarni qayta qayta qo'lda yaratmasdan, faqat bir marta di orqali yaratib foydalanish va kodning testdan o'tkazishiga yordam beradi. Dagger 2 kompilyatsiya jarayonida annotationlar va dependency graph asosida kod yaratish orqali ishlaydi. Dependencylarni provide qilishda yoki inject qilishda Java annotationlardan foydalanadi. Generatsiya qilingan kod dependencylarning obyektlarini yaratadi va boshqaradi.

:white_check_mark: Dagger 2-dagi ba'zi asosiy tushunchalar:

- **```@Component```** - Dagger 2 bilan ishlash uchun asosiy interfeysdir. U injectionning maqsadlarini belgilaydi va injected qilingan ob'ektlarni ko'rsatadi. Componentlar annotation kod asosida yaratiladi va so'ralganda kerakli dependencylarni ta'minlaydi.
- **```@Module```** - Componentlar tomonidan talab qilinadigan dependencylarni ta'minlovchi class hisoblanadi. Unda ma'lum turdagi obyektlarni qanday yaratish yoki provide qilishni ko'rsatuvchi @Provides bilan annotated qilingang method mavjud. Modullar componentlarga @Component annotatsiyasi yordamida bog'lanadi.
- **```@Inject```** - dependencylarni kiritishni talab qiladigan classdagi construktor, field yoki methodlarni belgilash uchun ishlatiladi. Dagger 2 ushbu annotationni tahlil qiladi va dependencylarni bajarish uchun avtomatik ravishda kodni yaratadi. Va graphdan shu dependencylarni olib keladi, va inject qiladi.
- **```@Scope```** - Dagger 2 dagi scopelar lifecycleni boshqarishga yordam beradi. Scopelar @Scope annotation yordamida aniqlanishi va componentlar yoki individual dependencylarga qo'llanilishi mumkin.

:white_check_mark: Dagger 2 va Koin ikkalasi ham Android-ni ishlab chiqishda qo'llaniladigan dependency injection frameworkidir, ammo ularning amalga oshirilishi va xususiyatlari bo'yicha ba'zi farqlar mavjud. Bu erda Dagger 2 va Coin o'rtasidagi asosiy farqlar haqida ma'lumot berishga harakat qilaman:
- **```Language:```** Dagger 2 Java-da, Koin esa Kotlin-da amalga oshiriladi. Biroq, ikkala framework ham har ikkala tilda yozilgan proektlarda ishlatilishi mumkin. 
- **```Annotation-based:```** Dagger 2 asosan dependencylarni aniqlash va kerakli injection kodini yaratish uchun annotationlarga tayanadi. Dagger 2 dependencylarni va ularni kiritish nuqtalarini belgilash uchun @Inject, @Component va @Module kabi annotationlardan foydalanadi. Koin ko'proq Kotlinga yo'naltirilgan yondashuvdan foydalanadi va Kotlinning extension funktsiyalari va depedency injection uchun properties kabi til xususiyatlaridan foydalanadi.
- **```Compilation:```** Dagger 2 dependency injection uchun zarur bo'lgan kodni yaratish uchun, kompilyatsiya bosqichida annotation protsessoridan foydalanadi. U dependencylar graphini yaratadi va foydalanilgan annotation asosida tegishli kodni yaratadi. Biroq, Koin Kotlinning delegated properties va extension funksiyalaridan foydalanadi, Koin kompilyatsiya paytida emas, balki runtimeda ishlaydi.
- **```Configuration:```** Dagger 2 Koin bilan solishtirganda ko'proq konfiguratsiya va sozlashlarnini talab qiladi. Dagger 2 componentlar, modullarni yaratish va component interfeysi orqali aniq dependencylarni taqdim etishni o'z ichiga oladi. Koin ko'proq Kotlinga asoslangan bo'lib, dependencylarni aniqlash va ularga kirishning yanada ixcham usulini ta'minlash uchun extension funktsiyalari kabi til xususiyatlaridan foydalanish orqali konfiguratsiya jarayonini soddalashtiradi.
- **```Performance:```** Dagger 2 code generatsiya yondashuvi kompilyatsiya vaqtida samarali va optimallashtirilgan dependencylarni kiritish imkonini beradi. U proektda qo'llaniladigan dependencylar uchun maxsus moslashtirilgan kodni ishlab chiqaradi, natijada runtime vaqtida injection vaqtlari tezroq bo'ladi. Koin, runtime yondashuvi bilan, runtime vaqtida dependencylarni dinamik ravishda hal qilganligi sababli, unchalik ham katta bo'lmagan ishlashga ega bo'lishi mumkin.
- **```Community and adoption:```** Dagger 2 uzoq vaqtdan beri mavjud va Android ishlab chiqish hamjamiyatida sezilarli darajada o'zlashtirildi. U ko'plab ishlab chiqarish dasturlarida keng qo'llaniladi va keng ko'lamli hujjatlar va dasturchilar yordamiga ega. Koin yangi framework bo'lib, Dagger 2 bilan solishtirganda kichikroq communitiyga ega.

:white_check_mark: Oxir oqibat, Dagger 2 va Koin o'rtasidagi tanlov proektimiz talablariga qaraladi va bizga qulay bo'lgan konfiguratsiya murakkabligi darajasiga va Java yoki Kotlinni afzal ko'rishimizga bog'liq. Agar biz Kotlinga asoslangan loyiha ustida ishlayotgan bo'lsak va qisqaroq va Kotlinga asoslangan yondashuvni afzal ko'rsak, Koin qaysidir jihatdan yaxshi tanlov bo'lishi mumkin. Ammo, agar biz Dagger 2 bilan yaxshi tanish bo'lsak yoki undan foydalanish bo'yicha yaxshi amaliyotga ega bo'lsak, Dagger 2-dan foydalanish juda ham foydali bo'ladi deb o'ylayman.
