---
title: Erreur du compilateur C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383046"
---
# <a name="compiler-error-c2720"></a>Erreur du compilateur C2720

> «*identificateur*' : '*spécificateur*' spécificateur de classe de stockage non conforme sur les membres

La classe de stockage ne peut pas être utilisée sur les membres de classe en dehors de la déclaration. Pour corriger cette erreur, supprimez les éléments inutiles [classe de stockage](../../cpp/storage-classes-cpp.md) spécificateur de la définition du membre en dehors de la déclaration de classe.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2720 et montre comment la corriger :

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```