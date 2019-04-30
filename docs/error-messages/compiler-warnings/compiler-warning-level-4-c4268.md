---
title: Avertissement du compilateur (niveau 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400914"
---
# <a name="compiler-warning-level-4-c4268"></a>Avertissement du compilateur (niveau 4) C4268

'identificateur' : 'const' données static/global initialisées avec le constructeur de valeur par défaut généré par le compilateur remplissent l’objet de zéros non significatifs

Un **const** instance globale ou statique d’une classe non triviale est initialisée avec un constructeur par défaut de généré par le compilateur.

## <a name="example"></a>Exemple

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Cette instance de la classe est **const**, la valeur de `m_data` ne peut pas être modifié.