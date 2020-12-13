---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4312'
title: Avertissement du compilateur (niveau 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 52e165fd30a9171c1a08aa16f78cc1f298271b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340071"
---
# <a name="compiler-warning-level-1-c4312"></a>Avertissement du compilateur (niveau 1) C4312

'opération' : la conversion de 'type1' en 'type2' d'une taille supérieure

Cet avertissement détecte une tentative d’assignation d’une valeur 32 bits à un type pointeur 64 bits, par exemple, en convertissant un pointeur 32 bits **`int`** ou **`long`** en pointeur 64 bits.

Cette conversion est potentiellement dangereuse, même pour des valeurs de pointeur qui tiennent dans 32 bits quand une extension de signe intervient. Si un entier 32 bits négatif est attribué à un type pointeur 64 bits, l'extension de signe se produit et la valeur de pointeur fait référence à une adresse mémoire différente de la valeur de l'entier.

Cet avertissement est émis uniquement pour les cibles de compilation 64 bits. Pour plus d’informations, consultez [règles d’utilisation des pointeurs](/windows/win32/WinProg64/rules-for-using-pointers).

L'exemple de code suivant génère l'erreur C4312 quand il est compilé pour des cibles 64 bits :

```cpp
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```
