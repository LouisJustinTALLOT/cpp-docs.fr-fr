---
title: Règles et limitations concernant les fonctions naked
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: 3dd089e13323e1811cf9d7c7717612313f2cef7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225850"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Règles et limitations concernant les fonctions naked

**Spécifique à Microsoft**

Les règles et les limitations suivantes s'appliquent aux fonctions naked :

- L' **`return`** instruction n’est pas autorisée.

- Les constructions de gestion structurée des exceptions et de gestion des exceptions C++ ne sont pas autorisées, car elles doivent se dérouler sur le frame de pile.

- Pour la même raison, toute forme de `setjmp` est interdite.

- L'utilisation de la fonction `_alloca` est interdite.

- Pour s'assurer qu'aucun code d'initialisation de variables locales n'apparaît avant la séquence de prologue, les variables locales initialisées ne soient pas autorisées dans la portée de la fonction. En particulier, la déclaration d'objets C++ n'est pas autorisée dans la portée de la fonction. En revanche, il peut y avoir des données initialisées dans une portée imbriquée.

- L'optimisation du pointeur de frame (option du compilateur /Oy) n'est pas recommandée, mais elle est supprimée automatiquement pour une fonction naked.

- Vous ne pouvez pas déclarer d'objets de classe C++ dans la portée lexicale de fonction. Vous pouvez toutefois déclarer des objets dans un bloc imbriqué.

- Le **`naked`** mot clé est ignoré lors de la compilation avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

- Pour [__fastcall](../cpp/fastcall.md) fonctions Naked, chaque fois qu’il existe une référence dans du code C/C++ à l’un des arguments de Registre, le code de prologue doit stocker les valeurs de ce registre dans l’emplacement de la pile pour cette variable. Par exemple :

```cpp
// nkdfastcl.cpp
// compile with: /c
// processor: x86
__declspec(naked) int __fastcall  power(int i, int j) {
   // calculates i^j, assumes that j >= 0

   // prolog
   __asm {
      push ebp
      mov ebp, esp
      sub esp, __LOCAL_SIZE
     // store ECX and EDX into stack locations allocated for i and j
     mov i, ecx
     mov j, edx
   }

   {
      int k = 1;   // return value
      while (j-- > 0)
         k *= i;
      __asm {
         mov eax, k
      };
   }

   // epilog
   __asm {
      mov esp, ebp
      pop ebp
      ret
   }
}
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Appels de fonction Naked](../cpp/naked-function-calls.md)
