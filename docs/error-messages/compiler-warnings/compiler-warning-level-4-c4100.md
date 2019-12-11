---
title: Avertissement du compilateur (niveau 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: bcd51c66359d0553b7657d85f5b45ee22d4648ff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991645"
---
# <a name="compiler-warning-level-4-c4100"></a>Avertissement du compilateur (niveau 4) C4100

'identificateur' : paramètre formel non référencé

Le paramètre formel n'est pas référencé dans le corps de la fonction. Le paramètre non référencé est ignoré.

C4100 peut également être émis lorsque le code appelle un destructeur sur un paramètre de type primitif qui autrement n'est pas référencé.  Il s’agit d’une limitation du C++ compilateur Microsoft.

L'exemple suivant génère l'avertissement C4100 :

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
