---
title: Erreur du compilateur C2270
ms.date: 11/04/2016
f1_keywords:
- C2270
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
ms.openlocfilehash: 704d397f06432575b7db531039b4454d4716c54e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388915"
---
# <a name="compiler-error-c2270"></a>Erreur du compilateur C2270

'fonction' : modificateurs non autorisés sur les fonctions non membres

Une fonction non membre est déclarée avec [const](../../cpp/const-cpp.md), [volatile](../../cpp/volatile-cpp.md), ou un autre modificateur de modèle de mémoire.

L’exemple suivant génère l’erreur C2270 :

```
// C2270.cpp
// compile with: /c
void func1(void) const;   // C2270, nonmember function

void func2(void);

class CMyClass {
public:
   void func2(void) const;
};
```