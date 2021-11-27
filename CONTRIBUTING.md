# თარგმანში მონაწილეობა

## გაფორმება

- აბზაცის სიმბოლო — ეს არის სივრცე (`.xml` ფაილებში ცხრილების შედგენა დაუშვებელია)

## რეკომენდაციები თარგმანის შესახებ

კოდის კომენტარები უნდა იყოს თარგმნილი,
გამოტანის აღწერა, მაგალითად, `echo "You reload page $num times";` ასევე უნდა იყოს ნათარგმნი.

კოდში ინგლისური სიტყვების თარგმნის წესში არის გამონაკლისი შემთხვევა, 
როდესაც ფუნქცია განსხვავებულად დაამუშავებს ინგლისურ და ქართულ ვარიანტებს, მაგალითად,
`strtolower("Michael") === "michael"`, ხოლო `strtolower("მიხეილი") !== "მიხეილი"`.

სათაური `<title><function>func_name</function> example</title>`
ყოველთვის ითარგმნება როგორც `<title>გამოყენების მაგალითი <function>func_name</function></title>`.

## თარგმანის განახლება

ორიგინალი ინგლისურენოვანი დოკუმენტაცია განთავსებულია ამ მისამართზე [doc-en](https://github.com/php/doc-en).

ქართულენოვანი დოკუმენტაციის ფაილებს აქვთ კონკრეტული ფორმატი. ყოველი ფაილის დასაწყისში უნდა იყოს შემდეგი ფორმის კონსტრუქცია:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- EN-Revision: 0abaad099e3ec6064ed8cf31553dcd5e3e3fdfba Maintainer: Jano Status: ready -->
<!-- Reviewed: yes -->
```

სადაც `0abaad099e3ec6064ed8cf31553dcd5e3e3fdfba` — ინგლისურენოვან დოკუმენტაციაში კომიტის სრული ნომერი არის, უახლესი აქტუალური რედაქტირების მომენტში მიმდინარე ფაილისთვის.
ეს აუცილებელია იმისათვის, რომ გავიგოთ, რა არის ნათარგმნი და რა არ არის ნათარგმნი.

### ცვლილებებზე თვალყურის დევნება

#### doc.php.net-ის დახმარებით

აირჩიეთ ქართული მარჯვენა მხარეს და შემდეგ გამოიყენეთ ინსტრუმენტი "Outdated files".
ცხრილში ჩამოთვლილი იქნება ფაილები, რომლებისთვისაც საჭიროა თარგმანის განახლება.

ცხრილში `en` მითითებულია მიმდინარე ინგლისური ვერსიის ჰეში, და სვეტში `ka` - თარგმანის ჰეში.

#### ბრძანების სტრიქონის გამოყენებით

განახორციელეთ რეპოზიტორიის კლონირება [doc-base](https://github.com/php/doc-base) ერთ დონეზე
[doc-en](https://github.com/php/doc-en)-თან და `doc-ka`, ისე, რომ საქაღალდის სტრუქტურა იყოს შემდეგი:

```
├── doc-base/
├── en/
└── ka/
```

გთხოვთ გაითვალისწინოთ, რომ ენის საქაღალდეები უნდა იყოს პრეფიქსის გარეშე `doc-`.

კლონირებისთვის შეგიძლიათ გამოიყენოთ ბრძანება `git clone https://github.com/php/doc-ka.git ka`.

გაუშვით შემდეგი ბრძანება ტერმინალში და გახსენით მიღებული `revcheck.html` ბრაუზერში:

```
php doc-base/scripts/revcheck.php ka > revcheck.html
```
განყოფილებაში "Outdated Files" თქვენ შეგიძლიათ ნახოთ აქტუალური ინგლისური ვერსია და მიმდინარე.

### ცვლილებების ნახვა

იმის სანახავად, თუ რა ცვლილებები განხორციელდა, გაუშვით შემდეგი ბრძანება:

```
git --no-pager diff 8b5940cadeb4f1c8492f4a7f70743a2be807cf39 68a9c82e06906a5c00e0199307d87dd3739f719b reference/array/functions/in-array.xml
```

სადაც არის პირველი ჰეში — ეს არის მიმდინარე ვერსია `EN-Revision-დან`, და მეორე არის აქტუალური ინგლისური ვერსიის ჰეში.

გამოტანის მაგალითი:

```diff
--- a/reference/array/functions/in-array.xml
+++ b/reference/array/functions/in-array.xml
@@ -14,7 +14,7 @@
  <methodparam choice="opt"><type>bool</type><parameter>strict</parameter><initializer>&false;</initializer></methodparam>
  </methodsynopsis>
  <para>
-  Searches <parameter>haystack</parameter> for <parameter>needle</parameter> using loose comparison
+  Searches for <parameter>needle</parameter> in <parameter>haystack</parameter> using loose comparison unless <parameter>strict</parameter> is set.
  </para>
  </refsect1>
```

როგორც ხედავთ, ფუნქციის აღწერა შეიცვალა.

სტრიაონი `Searches <parameter>haystack</parameter> for <parameter>needle</parameter> using loose comparison`
შეცვალა `Searches for <parameter>needle</parameter> in <parameter>haystack</parameter> using loose comparison`.

გახსენით `reference/array/functions/in-array.xml` ფაილი რეპოზიტორიაში `doc-ka`
და შეცვალეთ სტრიქონი ინგლისურ ვერსიასთან შესაბამისად.

შემდეგ განაახლეთ თქვენი კომენტარი `EN-Revision`.

## მთარგმნელობითი შეთანხმება

| ორიგინალი | თარგმანი |
| -------- | ------- |
| Application | აპლიკაცია |
| Cache | ჰეში |
| Callback function | Callback-ფუნქცია |
| Child | შვილი ელემენტი |
| CLI | ბრძანების სტრიქონის ინტერფეისი |
| Code (php-code) | კოდი, PHP-კოდი |
| Coding standards | კოდირების სტანდარტები |
| Commandline program | კონსოლის პროგრამა |
| Commit | ფიქსაცია (მაგალითად, ტრანზაქციები) |
| Default, by default | ნაგულისხმევად (იწერება დეფისის გარეშე) |
| Directory | დირექტორია |
| Entry | ელემენტი (არსებითი, მასივებისთვის, სიებისა და სხვა სტრუქტურებისთვის) |
| Extension | მოდული |
| Features/functionality | შესაძლებლობა, ფუნქციონალურობა |
| Float (floating point) | მცოცავ წერილიანი რიცხვი (მცოცავი წერტილი) |
| Getter | კითხვის მეთოდი |
| Hash | ჰეში |
| HTML entity | HTML-ერთეული |
| HTTP-Authentication | HTTP-აუთენთიფიკაცია |
| Hypertext preprocessor | ჰიპერტექსტის პროცესორი |
| Handle | დესკრიპტორი (მაგალიტად, cURL) |
| ID (მონ. ბაზა) | ID |
| ID (ტექსტში) | იდენთიფიკატორი |
| Legacy (system, server) | მოძველებული სისტემა, სერვერი, პროტოკოლი |
| Legacy support | ძველი ვერსიების მხარდაჭერა |
| Magic quotes | "ჯადოსნური" ციტატები |
| Magic constants/methods/numbers | "ჯადოსნური" კონსტანტები/მეთოდები/რიცხვები |
| Multibyte string | მულტიბაიტიანი სტრიქონი |
| Node | კვანძი |
| Optional | სურვილისამებრ |
| Override | ხელ ახლა განსაზღვრა |
| Otherwise | წინააღმდეგ შემთხვევაში, სხვაგვარად |
| On success | თუ წარმატებით შესრულდა |
| On fail | თუ შეცდომა მოხდა |
| Parameter(s) | Пპარამეტრი(ები), არგუმენტი(ები) |
| Parser | პარსერი |
| Parsing | ანალიზები (მაგ. სტრიქონის გარჩევა) |
| Prefetch | წინასწარი მიღება |
| PCRE | Perl თავსებადი რეგულარული გამოსახულებები |
| Private | დახურულია |
| Public | საჯარო |
| Read-only | მხოლოდ წაკითხვა |
| Result set | შედეგების ნაკრები |
| Returns | აბრუნებს |
| SAPI | სერვერის აპლიკაციის განვითარების ინტერფეისი |
| Script | სკრიპტი |
| Setter | დაყენების მეთოდი |
| Single quotes | ერთმაგი ბრჭყალები |
| Stream | ნაკადი |
| Shared block | ზოგადი ბლოკირება |
| Shared memory | საერთო მეხსიერება |
| SQL query | SQL მოთხოვნა |
| SQL | მოთხოვნის სტრუქტურირებული ენა |
| Throw exception | გამონაკლისის ჩაგდება |
| Timezone, time zone | დროის სარტყელი |
| Token | ლექსემა |
| Tokenizer | ლექსერი |
| Trait | მახასიათებელი |
| Writable | ხელმისაწვდომია ჩასაწერად |
| Wrapper | შეფუთვა |
| URL wrapper | URL შეფუთვა |
| To throw a warning/error | გაფრთხილების/შეცდომის გამოძახება |

## Не переводятся

- Cookie
- PEAR
- PECL
- PHP Group
- PHP
- Referer
- ცვლადის სახელები
- ცვლადის ტიპები (integer, string, bool, resource)
