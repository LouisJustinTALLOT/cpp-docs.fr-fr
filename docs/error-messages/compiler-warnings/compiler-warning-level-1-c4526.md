---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4526'
title: Avertissement du compilateur (niveau 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 13eddea0fcf82686333fe51d253c3b24552e18c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294819"
---
# <a name="compiler-warning-level-1-c4526"></a>Avertissement du compilateur (niveau 1) C4526

'fonction' : la fonction membre static ne peut pas substituer la fonction virtuelle’Virtual function’override ignorée, la fonction Virtual sera masquée

La fonction membre statique répond aux critères pour remplacer la fonction virtuelle, ce qui rend la fonction membre à la fois virtuelle et statique.

Le code suivant génère C4526 :

```cpp
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

Les correctifs possibles sont les suivants :

- Si la fonction était destinée à substituer la fonction virtuelle de la classe de base, supprimez le spécificateur statique.

- Si la fonction était destinée à être une fonction membre statique, renommez-la afin qu’elle ne soit pas en conflit avec la fonction virtuelle de la classe de base.
