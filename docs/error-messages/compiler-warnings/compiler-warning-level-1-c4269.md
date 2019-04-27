---
title: Avertissement du compilateur (niveau 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207231"
---
# <a name="compiler-warning-level-1-c4269"></a>Avertissement du compilateur (niveau 1) C4269

'identificateur' : les données automatiques 'const' initialisées avec le constructeur de valeur par défaut généré par le compilateur produisent des résultats incertains

Un **const** instance automatique d’une classe non triviale est initialisée avec un constructeur par défaut de généré par le compilateur.

## <a name="example"></a>Exemple

```
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

Étant donné que cette instance de la classe est générée sur la pile, la valeur initiale de `m_data` peut être quelconque. En outre, puisqu’il s’agit une **const** de l’instance, la valeur de `m_data` ne peut jamais être modifié.