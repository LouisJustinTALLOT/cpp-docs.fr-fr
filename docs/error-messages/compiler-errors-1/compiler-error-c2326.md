---
title: Erreur du compilateur C2326
ms.date: 11/04/2016
f1_keywords:
- C2326
helpviewer_keywords:
- C2326
ms.assetid: 01a5ea40-de83-4e6f-a4e8-469f441258e0
ms.openlocfilehash: 36df63ce1ac5bcdb444721be3aa10f9867ae7c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300895"
---
# <a name="compiler-error-c2326"></a>Erreur du compilateur C2326

'declarator' : la fonction ne peut pas accéder à 'name'

Le code tente de modifier une variable membre, ce qui n’est pas possible.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2326 :

```
// C2326.cpp
void MyFunc() {
   int i;

   class MyClass  {
   public:
      void mf() {
         i = 4;   // C2326 i is inaccessible
      }
   };
}
```