---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4441'
title: Avertissement du compilateur (niveau 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: f09e25696edffadaeb843d0dbb7ec47f4bcf8a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212569"
---
# <a name="compiler-warning-level-1-c4441"></a>Avertissement du compilateur (niveau 1) C4441

Convention d’appel de’CC1 'ignorée ; 'CC2 'utilisé à la place

Les fonctions membres dans les types managés définis par l’utilisateur et les génériques de fonction globale doivent utiliser la Convention d’appel [__clrcall](../../cpp/clrcall.md) .  Compilateur utilisé `__clrcall` .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4441.

```cpp
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```
