---
title: Erreur du compilateur C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 8a71fe05e2a046a65b659840f94d104a3c526778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744158"
---
# <a name="compiler-error-c2448"></a>Erreur du compilateur C2448

'identifier' : l’initialiseur de style fonction semble être une définition de fonction

La définition de la fonction est incorrecte.

Cette erreur peut être due à une liste formelle en langage C de type ancien.

L’exemple suivant génère l’C2448 :

```cpp
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```
