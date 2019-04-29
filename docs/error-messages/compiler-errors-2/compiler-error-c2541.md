---
title: Erreur du compilateur C2541
ms.date: 11/04/2016
f1_keywords:
- C2541
helpviewer_keywords:
- C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
ms.openlocfilehash: d8b2366bc2899b7a2ac76b0fae133351cd88a541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386952"
---
# <a name="compiler-error-c2541"></a>Erreur du compilateur C2541

'delete' : delete : Impossible de supprimer les objets qui ne sont pas des pointeurs

Le [supprimer](../../cpp/delete-operator-cpp.md) opérateur a été utilisé sur un objet qui n’est pas un pointeur.

L’exemple suivant génère l’erreur C2541 :

```
// C2541.cpp
int main() {
   int i;
   delete i;   // C2541 i not a pointer

   // OK
   int *ip = new int;
   delete ip;
}
```