---
title: Erreur du compilateur C2648
ms.date: 11/04/2016
f1_keywords:
- C2648
helpviewer_keywords:
- C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
ms.openlocfilehash: fc563c6e85555b113734ec93fc545bb505bd3f38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282151"
---
# <a name="compiler-error-c2648"></a>Erreur du compilateur C2648

'identificateur' : utilisation d’un membre comme paramètre par défaut nécessite un membre static

Un membre non statique est utilisé comme un paramètre par défaut.

L’exemple suivant génère l’erreur C2648 :

```
// C2648.cpp
// compile with: /c
class C {
public:
   int i;
   static int j;
   void func1( int i = i );  // C2648  i is not static
   void func2( int i = j );  // OK
};
```