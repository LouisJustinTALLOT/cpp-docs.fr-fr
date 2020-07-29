---
title: Erreur du compilateur C2555
description: Référence pour l’erreur du compilateur Visual Studio C++ C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ecac92bc663a6344e9ddafe13c194a92ab944c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207795"
---
# <a name="compiler-error-c2555"></a>Erreur du compilateur C2555

> '*classe1*::*function1*' : le type de retour de la fonction virtuelle de substitution diffère et n’est pas covariant de'*Class2*::*fonction2*'

Une fonction virtuelle et une fonction de substitution dérivée ont des listes de paramètres identiques, mais des types de retour différents.

## <a name="remarks"></a>Notes

En C++, une fonction de substitution dans une classe dérivée ne peut pas différer uniquement par le type de retour d’une fonction virtuelle dans une classe de base.

Il existe une exception à cette règle pour certains types de retour. Lorsqu’une classe dérivée substitue une classe de base publique, elle peut retourner un pointeur ou une référence à la classe dérivée au lieu d’un pointeur ou d’une référence de classe de base. Ces types de retours sont appelés *covariants*, car ils varient en fonction du type. Cette exception de règle n’autorise pas les types covariants de référence vers pointeur ou pointeur vers pointeur.

Une façon de résoudre l’erreur consiste à retourner le même type que la classe de base. Effectuez ensuite un cast de la valeur de retour après l’appel de la fonction virtuelle. Une autre consiste à modifier également la liste de paramètres pour faire de la fonction membre de classe dérivée une surcharge au lieu d’une substitution.

## <a name="examples"></a>Exemples

Cette erreur peut s’afficher si vous compilez avec **`/clr`** . Par exemple, l’équivalent C++ de la déclaration C# suivante :

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

L’exemple suivant génère l’C2555 :

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

Pour le résoudre, modifiez le type de retour de `Y::func` en **`void`** .
