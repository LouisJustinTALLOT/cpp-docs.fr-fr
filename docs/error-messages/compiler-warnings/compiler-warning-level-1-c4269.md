---
title: Avertissement du compilateur (niveau 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 84a0d4c541f67742d68c7f08e0dda52ccd350d04
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626709"
---
# <a name="compiler-warning-level-1-c4269"></a>Avertissement du compilateur (niveau 1) C4269

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