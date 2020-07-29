---
title: Erreur du compilateur C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 96f2ccc29eed5c1fa4e29f69d18ae6503417f211
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212720"
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

Une autre solution consiste à supprimer **`typedef`** pour définir une variable avec une liste d’initialiseurs d’agrégats, mais cela n’est pas recommandé, car elle crée une variable avec le même nom que le type et masque le nom du type.
