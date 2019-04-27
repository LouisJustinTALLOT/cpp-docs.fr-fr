---
title: Erreur du compilateur C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: 9d9ba48b0607e7a30b8748d4e9ae4f7025f11dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165019"
---
# <a name="compiler-error-c2511"></a>Erreur du compilateur C2511

'identificateur' : la fonction membre introuvable dans 'class' surchargée

Aucune version de la fonction n’est déclarée avec les paramètres spécifiés.  Causes possibles :

1. Paramètres erronés passés à la fonction.

1. Les paramètres passés dans un ordre incorrect.

1. Orthographe incorrecte des noms de paramètres.

L’exemple suivant génère l’erreur C2511 :

```
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```