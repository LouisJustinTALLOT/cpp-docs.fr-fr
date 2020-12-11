---
description: 'En savoir plus sur : erreur du compilateur C2720'
title: Erreur du compilateur C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 187142af02289374235725340a206f35b6a42493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155655"
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
