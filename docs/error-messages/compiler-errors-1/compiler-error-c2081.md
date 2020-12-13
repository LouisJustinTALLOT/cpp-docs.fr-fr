---
description: 'En savoir plus sur : erreur du compilateur C2081'
title: Erreur du compilateur C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: e6f75d6d478d9523d36a9671457cf2a5618e4f21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151175"
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
