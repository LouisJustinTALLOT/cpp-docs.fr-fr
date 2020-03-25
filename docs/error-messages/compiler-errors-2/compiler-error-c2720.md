---
title: Erreur du compilateur C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202131"
---
# <a name="compiler-error-c2720"></a>Erreur du compilateur C2720

> '*identificateur*' : spécificateur de classe de stockage'*specifier*'non conforme sur les membres

La classe de stockage ne peut pas être utilisée sur les membres de classe en dehors de la déclaration. Pour corriger cette erreur, supprimez le spécificateur de [classe de stockage](../../cpp/storage-classes-cpp.md) inutile de la définition du membre en dehors de la déclaration de classe.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2720 et montre comment la corriger :

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
