---
title: Erreur du compilateur C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 1f798774a7735a6aceb0bf75b3c6da9ccb1e4a72
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301975"
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
