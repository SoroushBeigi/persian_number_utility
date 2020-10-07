# A Flutter Package for convert number to English or Persian (Farsi) letter

A Flutter Package for convert number to English or Persian (Farsi) letter and allow you to separate an integer by comma (or other) for every three digits and extract number from string

پکیجی برای تبدیل اعداد به حروف فارسی یا انگلیسی ، همچنین برای جدا سازی سه رقمی ارقام و جداسازی ارقام از متن

See the [Dart packages](https://pub.dev/packages/persian_number_utility).

## Screenshot

![](screenshot.png)

## Usage

Add it to your pubspec.yaml file:

```yaml
dependencies:

persian_number_utility: ^0.2.1
```

In your library add the following import:

```dart

import  'package:persian_number_utility/persian_number_utility.dart';

```

Here is an example how to use:

```dart

import 'package:flutter/material.dart';
import 'package:persian_number_utility/persian_number_utility.dart'; //import

class NumToStr extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    String number = "100092";//number here

    return Scaffold(
        body: Center(
            child: Column(
      crossAxisAlignment: CrossAxisAlignment.center,
      mainAxisAlignment: MainAxisAlignment.center,
      mainAxisSize: MainAxisSize.max,
      children: <Widget>[
        Text(number),//the number

        //تبدیل عدد به حروف فارسی - convert number to persian (farsi) letter
        Text(NumberUtility.toWord(number, NumStrLanguage.Farsi)),//صد هزار و نود و دو
        Text(number.toWord()),//صد هزار و نود و دو

        //تبدیل عدد به حروف انگلیسی - convert number to english letter
        Text(NumberUtility.toWord(number, NumStrLanguage.English)),//one hundred thousand ninety two
        Text(number.toWord(lang: NumStrLanguage.English)),//one hundred thousand ninety two

        //رشته ورودی عددی هست یا نه - string is numeric or not
        Text(NumberUtility.isNumeric(number).toString()),//true
        Text(number.isNumeric().toString()),//true

        //جدا سازی سه رقمی ارقام با ویرگول - separate an integer by comma for every three digits
        Text(NumberUtility.seRagham(number)),//100,092
        Text(number.seRagham()),//100,092

        //جدا سازی سه رقمی ارقام با علامت انتخابی - separate an integer by custom character for every three digits
        Text(NumberUtility.seRagham(number, separator: ".")),//100.092
        Text(number.seRagham(separator: ".")),//100.092

        //تبدیل اعداد انگلیسی به فارسی - convert english digit to persian digit
        Text(NumberUtility.changeDigit(number, NumStrLanguage.Farsi)),//123456789 to ۱۲۳۴۵۶۷۸۹
        Text(number.toEnglishDigit()),//123456789 to ۱۲۳۴۵۶۷۸۹

        //تبدیل اعداد فارسی یا عربی به انگلیسی - convert persian/arabic digit to english digit
        Text(NumberUtility.changeDigit(number, NumStrLanguage.English)),//۱۲۳۴۵۶۷۸۹ to 123456789
        Text(number.toEnglishDigit()),//۱۲۳۴۵۶۷۸۹ to 123456789

        //جدا سازی اعداد از رشته - extract number from string
        Text(NumberUtility.extractNumber("123456+.abc", NumStrLanguage.Farsi)),//۱۲۳۴۵۶
        Text("123456+.abc".extractNumber()),//۱۲۳۴۵۶

        //جدا سازی اعداد از رشته - extract number from string
        Text(NumberUtility.extractNumber("number123456اب ج -", NumStrLanguage.English)),//123456
        Text("number123456اب ج -".extractNumber(toDigit: NumStrLanguage.English)),//123456

        //_______________________ تبدیل تاریخ __________________________

        //تبدیل تاریخ میلادی به تاریخ شمسی
        Text(DateTime.now().toPersianDate()),//۱۳۹۹/۰۷/۱۶

        //تبدیل تاریخ میلادی به تاریخ شمسی از متن
        Text("2020-10-07T07:47:03.233Z".toPersinaDate()),//۱۳۹۹/۰۷/۱۶

        //تبدیل تاریخ میلادی به متن تاریخ شمسی
        Text(DateTime.now().toPersianDateStr(strDay: true,strMonth: true)),// شانزده مهر  ۱۳۹۹
        Text(DateTime.now().toPersianDateStr(showDayStr: true))//چهارشنبه ۱۶ مهر  ۱۳۹۹

      ],
    )));
  }
}


```

## Getting Started

This project is a starting point for a Dart
[package](https://flutter.dev/developing-packages/),
a library module containing code that can be shared easily across
multiple Flutter or Dart projects.

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
