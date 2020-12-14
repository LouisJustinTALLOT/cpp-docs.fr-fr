---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4100'
title: Avertissement du compilateur (niveau 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 753be5e6e56e4ad94d6b742454fe62e303d430dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261994"
---
# <a name="compiler-warning-level-4-c4100"></a>Avertissement du compilateur (niveau 4) C4100

'identificateur' : paramètre formel non référencé

Le paramètre formel n’est pas référencé dans le corps de la fonction. Le paramètre non référencé est ignoré.

C4100 peut également être émis lorsque le code appelle un destructeur sur un paramètre non référencé de type primitif.  Il s’agit d’une limitation du compilateur Microsoft C++.

L’exemple suivant génère l’C4100 :

```cpp
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
