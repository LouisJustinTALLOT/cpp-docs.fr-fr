---
description: 'En savoir plus sur : erreur du compilateur C3538'
title: Erreur du compilateur C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 6fbfbc59bb52d4603fc734e69f2f7ccc88942f7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112464"
---
# <a name="compiler-error-c3538"></a>Erreur du compilateur C3538

dans une liste de déclarateurs, 'auto' doit toujours être déduit au même type

Toutes les variables déclarées dans une liste de déclaration ne correspondent pas au même type.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que toutes les **`auto`** déclarations de la liste déduisent vers le même type.

## <a name="example"></a>Exemple

Les instructions suivantes génèrent l'erreur C3538. Chaque instruction déclare plusieurs variables, mais chaque utilisation du **`auto`** mot clé n’est pas déduire vers le même type.

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-cpp.md)
