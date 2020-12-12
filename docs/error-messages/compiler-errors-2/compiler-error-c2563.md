---
description: 'En savoir plus sur : erreur du compilateur C2563'
title: Erreur du compilateur C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 2243e0820b2e69d6bc05351fdba4600188a3ac08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209150"
---
# <a name="compiler-error-c2563"></a>Erreur du compilateur C2563

incompatibilité dans la liste de paramètres formels

La liste de paramètres formels d’une fonction (ou d’un pointeur vers une fonction) ne correspond pas à celles d’une autre fonction (ou d’un pointeur vers une fonction membre). Par conséquent, l’assignation de fonctions ou de pointeurs ne peut pas être effectuée.

L’exemple suivant génère l’C2563 :

```cpp
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
