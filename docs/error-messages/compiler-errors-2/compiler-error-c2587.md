---
title: Erreur du compilateur C2587
ms.date: 11/04/2016
f1_keywords:
- C2587
helpviewer_keywords:
- C2587
ms.assetid: 7637a2c7-35d4-4b5a-a8f2-515a7bda98fd
ms.openlocfilehash: 08a576d5672f0df1cbec7269f83a3f182ce0e1c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350504"
---
# <a name="compiler-error-c2587"></a>Erreur du compilateur C2587

'identificateur' : utilisation non conforme d’une variable locale comme paramètre par défaut

Variables locales ne sont pas autorisés comme paramètres par défaut.

L’exemple suivant génère l’erreur C2587 :

```
// C2587.cpp
// compile with: /c
int i;
void func() {
   int j;
   extern void func2( int k = j );  // C2587 -- local variable
   extern void func3( int k = i );   // OK
}
```