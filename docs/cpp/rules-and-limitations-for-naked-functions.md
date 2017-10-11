---
title: "Règles et Limitations pour les fonctions Naked | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a02eb245ffae169f75f5d8edb261d0af9618856d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="rules-and-limitations-for-naked-functions"></a>Règles et limitations concernant les fonctions naked
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Les règles et les limitations suivantes s'appliquent aux fonctions naked :  
  
-   L'instruction `return` n'est pas autorisée.  
  
-   Les constructions de gestion structurée des exceptions et de gestion des exceptions C++ ne sont pas autorisées, car elles doivent se dérouler sur le frame de pile.  
  
-   Pour la même raison, toute forme de `setjmp` est interdite.  
  
-   L'utilisation de la fonction `_alloca` est interdite.  
  
-   Pour s'assurer qu'aucun code d'initialisation de variables locales n'apparaît avant la séquence de prologue, les variables locales initialisées ne soient pas autorisées dans la portée de la fonction. En particulier, la déclaration d'objets C++ n'est pas autorisée dans la portée de la fonction. En revanche, il peut y avoir des données initialisées dans une portée imbriquée.  
  
-   L'optimisation du pointeur de frame (option du compilateur /Oy) n'est pas recommandée, mais elle est supprimée automatiquement pour une fonction naked.  
  
-   Vous ne pouvez pas déclarer d'objets de classe C++ dans la portée lexicale de fonction. Vous pouvez toutefois déclarer des objets dans un bloc imbriqué.  
  
-   Le `naked` mot clé est ignoré lors de la compilation avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Pour [__fastcall](../cpp/fastcall.md) fonctions naked, chaque fois qu’il existe une référence dans le code C/C++ à un des arguments de Registre, le code de prologue doit stocker les valeurs de ce Registre à l’emplacement de pile pour cette variable. Exemple :  
  
```  
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
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Appels de fonction naked](../cpp/naked-function-calls.md)
