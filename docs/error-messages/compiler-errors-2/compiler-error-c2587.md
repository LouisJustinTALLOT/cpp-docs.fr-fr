---
description: 'En savoir plus sur : erreur du compilateur C2587'
title: Erreur du compilateur C2587
ms.date: 11/04/2016
f1_keywords:
- C2587
helpviewer_keywords:
- C2587
ms.assetid: 7637a2c7-35d4-4b5a-a8f2-515a7bda98fd
ms.openlocfilehash: a5d447f2e1a08c310fdd5c2d42afef768f191f4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177599"
---
# <a name="compiler-error-c2587"></a>Erreur du compilateur C2587

'identificateur' : utilisation non conforme d’une variable locale comme paramètre par défaut

Les variables locales ne sont pas autorisées en tant que paramètres par défaut.

L’exemple suivant génère l’C2587 :

```cpp
// C2587.cpp
// compile with: /c
int i;
void func() {
   int j;
   extern void func2( int k = j );  // C2587 -- local variable
   extern void func3( int k = i );   // OK
}
```
