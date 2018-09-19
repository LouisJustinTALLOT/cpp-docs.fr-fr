---
title: Erreur du compilateur C2720 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d75c9847016102d4ae8609fb0a0a78726e4c67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084014"
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