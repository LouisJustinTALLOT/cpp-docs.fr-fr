---
title: Erreur du compilateur C2555
description: Référence pour l’erreur de compilateur C2555 de Visual Studio C.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374173"
---
# <a name="compiler-error-c2555"></a>Erreur du compilateur C2555

> '*class1*::*function1*': overriding virtual function return type differs and is not covariant from '*class2*::*function2*'

Une fonction virtuelle et une fonction dérivée ont des listes de paramètres identiques, mais différents types de retour.

## <a name="remarks"></a>Notes

Dans le C, une fonction primordiale dans une classe dérivée ne peut pas différer uniquement par type de retour d’une fonction virtuelle dans une classe de base.

Il y a une exception à cette règle pour certains types de retour. Lorsqu’une classe dérivée d’une classe de base publique, elle peut retourner un pointeur ou une référence à la classe dérivée au lieu d’un pointeur ou d’une référence de classe de base. Ces types de retour sont appelés *covariant*, parce qu’ils varient avec le type. Cette exception de règle n’autorise pas les types de référence à pointeur ou de pointeur à pointeur.

Une façon de résoudre l’erreur est de retourner le même type que la classe de base. Ensuite, jetez la valeur de retour après que la fonction virtuelle a été appelée. Une autre consiste également à modifier la liste des paramètres, pour faire de la fonction de membre de la classe dérivée une surcharge au lieu d’un remplacement.

## <a name="examples"></a>Exemples

Vous pouvez voir cette erreur si **`/clr`** vous compilez avec . Par exemple, l’équivalent de la déclaration suivante de CMD :

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

L’échantillon suivant génère C2555 :

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

Pour le réparer, modifier `Y::func` le `void`type de retour de .
