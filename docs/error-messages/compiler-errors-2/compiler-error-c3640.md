---
description: 'En savoir plus sur : erreur du compilateur C3640'
title: Erreur du compilateur C3640
ms.date: 11/04/2016
f1_keywords:
- C3640
helpviewer_keywords:
- C3640
ms.assetid: fcc56894-0f98-48af-8561-3bf7c7b2b93f
ms.openlocfilehash: 7f26a824cc39f2b5509c6d935a95cbc5af48aca0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239179"
---
# <a name="compiler-error-c3640"></a>Erreur du compilateur C3640

'membre' : une fonction membre référencée ou virtuelle d’une classe locale doit être définie

Le compilateur requiert la définition de certaines fonctions.

L’exemple suivant génère l’C3640 :

```cpp
// C3640.cpp
void f()
{
   struct S
   {
      virtual void f1();   // C3640
      // Try the following line instead:
      // virtual void f1(){}
   };
}
```
