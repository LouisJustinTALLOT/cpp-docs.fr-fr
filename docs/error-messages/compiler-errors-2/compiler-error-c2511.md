---
description: 'En savoir plus sur : erreur du compilateur C2511'
title: Erreur du compilateur C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: 846173cc887fd09b564d18e063820bc0e0d5b184
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212920"
---
# <a name="compiler-error-c2511"></a>Erreur du compilateur C2511

'identificateur' : fonction membre surchargée introuvable dans’classe'

Aucune version de la fonction n’est déclarée avec les paramètres spécifiés.  Causes possibles :

1. Paramètres incorrects passés à la fonction.

1. Les paramètres sont passés dans un ordre incorrect.

1. Orthographe incorrecte des noms de paramètres.

L’exemple suivant génère l’C2511 :

```cpp
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
