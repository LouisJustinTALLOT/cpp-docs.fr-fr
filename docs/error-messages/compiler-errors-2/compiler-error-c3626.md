---
description: 'En savoir plus sur : erreur du compilateur C3626'
title: Erreur du compilateur C3626
ms.date: 11/04/2016
f1_keywords:
- C3626
helpviewer_keywords:
- C3626
ms.assetid: 43926e2b-1ba9-4a43-9343-c58449cbb336
ms.openlocfilehash: 8db976a5f072db618ac4270df3bd1d8edf0ab15c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144415"
---
# <a name="compiler-error-c3626"></a>Erreur du compilateur C3626

'keyword' : le mot clé' __event’ne peut être utilisé que sur les interfaces COM, les fonctions membres et les données membres qui sont des pointeurs vers les délégués

Un mot clé a été utilisé de façon incorrecte.

L’exemple suivant génère l’C3626 :

```cpp
// C3626.cpp
// compile with: /c
struct A {
   __event int i;   // C3626
// try the following line instead
// __event int i();
};
```
