---
title: Point de déclaration en C++
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560652"
---
# <a name="point-of-declaration-in-c"></a>Point de déclaration en C++

Un nom est considéré comme déclaré immédiatement après son déclarateur mais avant son initialiseur (facultatif). (Pour plus d’informations sur les déclarateurs, consultez [déclarations et définitions](declarations-and-definitions-cpp.md).)

Considérez cet exemple :

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

Si le point de déclaration ont été *après* l’initialisation, puis local `dVar` serait initialisée à 7,0, la valeur de la variable globale `dVar`. Toutefois, comme ce n'est pas le cas, `dVar` est initialisé avec une valeur non définie.

## <a name="see-also"></a>Voir aussi

[Portée](../cpp/scope-visual-cpp.md)