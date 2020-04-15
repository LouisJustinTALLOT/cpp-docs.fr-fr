---
title: 'Comment : définir et consommer des énumérateurs dans C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370173"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Comment : définir et consommer des énumérateurs dans C++/CLI

Ce sujet traite des enums dans le CMD/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Spécifier le type sous-jacent d’un enum

Par défaut, le type sous-jacent `int`d’un recensement est .  Cependant, vous pouvez spécifier le type à `int` `short`signer `long` `__int32`ou non signé des formes de , , , , ou `__int64`.  Vous pouvez également utiliser `char`.

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Sortie**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Comment se convertir entre les énumérations gérées et les énumérations standard

Il n’y a pas de conversion standard entre un enum et un type intégral; un plâtre est nécessaire.

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Sortie**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Opérateurs et enums

Les opérateurs suivants sont valables sur les enums dans CMD/CLI :

|Opérateur|
|--------------|
|À l'>\<  >  \<|
|+ -|
|&#124; &|
|++ --|
|sizeof|

Les opérateurs &#124; & - sont définis uniquement pour les énumérations avec des types sous-jacents intégral, sans compter le bool.  Les deux opérandes doivent être du type d’énumération.

Le compilateur ne vérifie pas le résultat d’une opération enum; une opération peut entraîner une valeur qui ne se situe pas dans la plage des enumérateurs valides de l’enum.

> [!NOTE]
> Le C 11 introduit des types de classe enum dans le code non géré qui sont significativement différents des classes enum gérées dans le CMD/CLI. En particulier, le type de classe enum de la C-11 ne prend pas en charge les mêmes opérateurs que le type de classe enum géré dans le CMD/CLI, et le code source CMD/CLI doit fournir un spécificateur d’accessibilité dans les déclarations de classe enum gérées afin de les distinguer des déclarations de classe enum non gérées(C-11). Pour plus d’informations sur les cours d’enum dans le CMD/CLI, le CMD/CX et le C 11, consultez [la classe enum](../extensions/enum-class-cpp-component-extensions.md).

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Sortie**

```Output
4
1
True
```

## <a name="see-also"></a>Voir aussi

[enum, classe](../extensions/enum-class-cpp-component-extensions.md)
