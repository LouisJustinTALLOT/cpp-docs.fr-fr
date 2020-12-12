---
description: 'En savoir plus sur : erreur du compilateur C2088'
title: Erreur du compilateur C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 246c130c0918310b59924f3940950d443c0b9217
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251919"
---
# <a name="compiler-error-c2088"></a>Erreur du compilateur C2088

'operator' : non conforme pour’Class-Key'

L’opérateur n’a pas été défini pour la structure ou l’Union. Cette erreur est valide uniquement pour le code C.

L’exemple suivant génère C2088 trois fois :

```c
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```
