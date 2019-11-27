---
title: Avertissement du compilateur (niveau 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541246"
---
# <a name="compiler-warning-level-4-c4100"></a>Avertissement du compilateur (niveau 4) C4100

'identificateur' : paramètre formel non référencé

Le paramètre formel n’est pas référencé dans le corps de la fonction. Le paramètre non référencé est ignoré.

C4100 peut également être émis lorsque le code appelle un destructeur sur un paramètre non référencé de type primitif.  Il s’agit d’une limitation du C++ compilateur Microsoft.

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