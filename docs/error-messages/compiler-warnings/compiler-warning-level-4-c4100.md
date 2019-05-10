---
title: Avertissement du compilateur (niveau 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: ccb438cf7c80edb1403683ac4817617ffccc690d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447731"
---
# <a name="compiler-warning-level-4-c4100"></a>Avertissement du compilateur (niveau 4) C4100

'identificateur' : paramètre formel non référencé

Le paramètre formel n’est pas référencé dans le corps de la fonction. Le paramètre non référencé est ignoré.

C4100 peut également être émis lorsque le code appelle un destructeur sur un autre paramètre de type primitif non référencées.  Il s’agit d’une limitation de Microsoft C++ compilateur.

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