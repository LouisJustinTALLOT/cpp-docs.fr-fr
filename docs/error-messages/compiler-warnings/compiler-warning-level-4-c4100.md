---
title: Avertissement du compilateur (niveau 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 84a0b27203cd43e8a8992c4ba599f1400c6909ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401395"
---
# <a name="compiler-warning-level-4-c4100"></a>Avertissement du compilateur (niveau 4) C4100

'identificateur' : paramètre formel non référencé

Le paramètre formel n’est pas référencé dans le corps de la fonction. Le paramètre non référencé est ignoré.

C4100 peut également être émis lorsque le code appelle un destructeur sur un autre paramètre de type primitif non référencées.  Il s’agit d’une limitation du compilateur Visual C++.

L’exemple suivant génère l’avertissement C4100 :

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```