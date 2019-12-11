---
title: 'Comment : définir et consommer des énumérateurs dans C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 68f8e113f6199d3b320bc6d241ee3396d2b70a1a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988223"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Comment : définir et consommer des énumérateurs dans C++/CLI

Cette rubrique décrit les énumérations dans C++/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Spécification du type sous-jacent d’une énumération

Par défaut, le type sous-jacent d’une énumération est `int`.  Toutefois, vous pouvez spécifier le type qui doit être signé ou non signé de `int`, `short`, `long`, `__int32`ou `__int64`.  Vous pouvez également utiliser `char`.

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

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Comment effectuer une conversion entre des énumérations managées et standard

Il n’existe pas de conversion standard entre une énumération et un type intégral ; un cast est nécessaire.

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

## <a name="operators-and-enums"></a>Opérateurs et énumérations

Les opérateurs suivants sont valides sur les enums dans C++/CLI :

|opérateur|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Les &#124; opérateurs ^ & ~ + +--sont définis uniquement pour les énumérations avec des types sous-jacents, à l’exclusion de bool.  Les deux opérandes doivent être du type énumération.

Le compilateur n’effectue aucune vérification statique ou dynamique du résultat d’une opération Enum. une opération peut entraîner une valeur qui n’est pas comprise dans la plage des énumérateurs valides de l’énumération.

> [!NOTE]
>  C++ 11 introduit les types de classes enum dans du code non managé, qui sont très différents des classes C++enum managées dans/CLI. En particulier, le type de classe enum C++ 11 ne prend pas en charge les mêmes opérateurs que le type de C++classe enum managé C++dans/CLI, et le code source/CLI doit fournir un spécificateur d’accessibilité dans les déclarations de classe enum managées afin de les distinguer des déclarations de classe enum non managée (c++ 11). Pour plus d’informations sur les classes C++enum dans C++/CLI,/CX et c++ 11, consultez [enum, classe](../extensions/enum-class-cpp-component-extensions.md).

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
