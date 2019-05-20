---
title: ref new, gcnew  (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f3dd0b73e300b44cb4f35e42683725813453d7de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516644"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew  (C++/CLI et C++/CX)

Le mot clé d’agrégation **ref new** alloue une instance d’un type récupéré par le garbage collector quand l’objet devient inaccessible, et qui renvoie un handle ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) à l’objet alloué.

## <a name="all-runtimes"></a>Tous les runtimes

La mémoire d’une instance d’un type alloué par **ref new** est automatiquement désallouée.

Une opération **ref new** lève une exception `OutOfMemoryException` s’il est impossible d’allouer de la mémoire.

Pour plus d’informations sur l’allocation et la désallocation de la mémoire pour les types C++ natifs, consultez les [opérateurs new et delete](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Windows Runtime

Utilisez **ref new** pour allouer de la mémoire aux objets Windows Runtime dont vous voulez administrer automatiquement la durée de vie. L'objet est automatiquement désalloué quand son nombre de références atteint zéro, ce qui se produit une fois que la dernière copie de la référence est hors de portée. Pour plus d’informations, consultez [Classes et structures de référence](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

La mémoire d’un type managé (type référence ou valeur) est allouée par **gcnew**, puis désallouée à l’aide du garbage collection.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant utilise **gcnew** pour allouer un objet Message.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

L’exemple suivant utilise **gcnew** pour créer un type valeur boxed à utiliser comme type référence.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)