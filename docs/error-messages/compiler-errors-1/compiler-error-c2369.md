---
description: 'En savoir plus sur : erreur du compilateur C2369'
title: Erreur du compilateur C2369
ms.date: 11/04/2016
f1_keywords:
- C2369
helpviewer_keywords:
- C2369
ms.assetid: 2a3933f6-2313-40ff-800f-921b296fdbbf
ms.openlocfilehash: 42ae61307793383954c473eee948ee511815ab95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326083"
---
# <a name="compiler-error-c2369"></a>Erreur du compilateur C2369

'array' : redéfinition ; indices différents

Le tableau est déjà déclaré avec un indice différent.

L’exemple suivant génère l’erreur C2369 :

```cpp
// C2369.cpp
// compile with: /c
int a[10];
int a[20];   // C2369
int b[20];   // OK
```
