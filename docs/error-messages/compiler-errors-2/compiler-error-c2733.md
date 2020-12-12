---
description: 'En savoir plus sur : erreur du compilateur C2733'
title: Erreur du compilateur C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: f957be13b8c1de1ee3ada98ffd42f0d89fc7755c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123199"
---
# <a name="compiler-error-c2733"></a>Erreur du compilateur C2733

deuxième liaison C de la fonction surchargée’fonction’non autorisée

Plusieurs fonctions surchargées sont déclarées avec une liaison C. Lors de l’utilisation de la liaison C, une seule forme d’une fonction spécifiée peut être externe. Étant donné que les fonctions surchargées ont le même nom non décoré, elles ne peuvent pas être utilisées avec des programmes C.

L’exemple suivant génère l’C2733 :

```cpp
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```
