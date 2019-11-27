---
title: Avertissement du compilateur (niveau 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1d0531b79ef29d2aa9528cc29046fa9e9514c379
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541984"
---
# <a name="compiler-warning-level-4-c4268"></a>Avertissement du compilateur (niveau 4) C4268

'identificateur' : les données statiques/globales’const’initialisées avec le constructeur par défaut généré par le compilateur remplissent l’objet de zéros

Une instance **const** globale ou statique d’une classe non triviale est initialisée avec un constructeur par défaut généré par le compilateur.

## <a name="example"></a>Exemple

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Comme cette instance de la classe est **const**, la valeur de `m_data` ne peut pas être modifiée.