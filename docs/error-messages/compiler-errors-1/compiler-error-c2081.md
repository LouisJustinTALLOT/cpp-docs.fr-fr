---
title: Erreur du compilateur C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2bccd15b8c2b6d1c5cd6c4b536bbdaf350eb0181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512903"
---
# <a name="compiler-error-c2081"></a>Erreur du compilateur C2081

'identificateur' : nom non conforme de liste de paramètres formels dans

L’identificateur a causé une erreur de syntaxe.

Cette erreur peut être due à l’aide de l’ancien style pour la liste de paramètres formels. Vous devez spécifier le type de paramètres formels dans la liste de paramètres formels.

L’exemple suivant génère l’erreur C2081 :

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Solution possible :

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```