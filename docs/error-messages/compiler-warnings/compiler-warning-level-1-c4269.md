---
title: Avertissement du compilateur (niveau 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199769"
---
# <a name="compiler-warning-level-1-c4269"></a>Avertissement du compilateur (niveau 1) C4269

'identificateur' : les données automatiques’const’initialisées avec le constructeur par défaut généré par le compilateur produisent des résultats non fiables

Une instance automatique **const** d’une classe non triviale est initialisée avec un constructeur par défaut généré par le compilateur.

## <a name="example"></a>Exemple

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

Étant donné que cette instance de la classe est générée sur la pile, la valeur initiale de `m_data` peut être n’importe quoi. En outre, étant donné qu’il s’agit d’une instance **const** , la valeur de `m_data` ne peut jamais être modifiée.
