---
title: Erreur du compilateur C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301988"
---
# <a name="compiler-error-c2081"></a>Erreur du compilateur C2081

'identificateur' : nom non conforme dans la liste de paramètres formels

L’identificateur a provoqué une erreur de syntaxe.

Cette erreur peut être due à l’utilisation de l’ancien style pour la liste de paramètres formels. Vous devez spécifier le type de paramètres formels dans la liste de paramètres formels.

L’exemple suivant génère l’C2081 :

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Solution possible :

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
