---
title: Erreur du compilateur C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 093a5856fdcfa6311fcef93214672b035c91b4fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746524"
---
# <a name="compiler-error-c2513"></a>Erreur du compilateur C2513

'type' : aucune variable déclarée avant' = '

Le spécificateur de type apparaît dans la déclaration sans identificateur de variable.

L’exemple suivant génère l’C2513 :

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Cette erreur peut également être générée à la suite d’un travail de mise en conformité du compilateur pour Visual Studio .NET 2003 : l’initialisation d’un typedef n’est plus autorisée. L’initialisation d’un typedef n’est pas autorisée par la norme et génère désormais une erreur du compilateur.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Une autre solution consiste à supprimer `typedef` pour définir une variable avec une liste d’initialiseurs d’agrégats, mais cela n’est pas recommandé, car il créera une variable portant le même nom que le type et masquera le nom du type.
