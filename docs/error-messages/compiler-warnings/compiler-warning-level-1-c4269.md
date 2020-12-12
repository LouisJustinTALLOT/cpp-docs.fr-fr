---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4269'
title: Avertissement du compilateur (niveau 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 6b00eeee4a831ee7876556838f03d4b74f4790fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266128"
---
# <a name="compiler-warning-level-1-c4269"></a>Avertissement du compilateur (niveau 1) C4269

'identificateur' : les données automatiques’const’initialisées avec le constructeur par défaut généré par le compilateur produisent des résultats non fiables

Une **`const`** instance automatique d’une classe non triviale est initialisée avec un constructeur par défaut généré par le compilateur.

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

Étant donné que cette instance de la classe est générée sur la pile, la valeur initiale de `m_data` peut être n’importe quoi. En outre, étant donné qu’il s’agit **`const`** d’une instance, la valeur de ne `m_data` peut jamais être modifiée.
