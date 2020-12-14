---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4062'
title: Avertissement du compilateur (niveau 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 3aee4286fb8d06d98617ea6fa71929768cbd23c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262046"
---
# <a name="compiler-warning-level-4-c4062"></a>Avertissement du compilateur (niveau 4) C4062

> l’énumérateur'*identifier*'dans le commutateur de l’enum'*Enumeration*'n’est pas géré

L' *identificateur* d’énumérateur n’est associé `case` à aucun gestionnaire dans une **`switch`** instruction et il n’y a pas d' **`default`** étiquette qui peut l’intercepter. Le cas manquant peut être une supervision et constitue une erreur potentielle dans votre code. Pour obtenir un avertissement connexe sur les énumérateurs inutilisés dans les **`switch`** instructions qui ont un **`default`** cas, consultez [C4061](compiler-warning-level-4-c4061.md).

Cet avertissement est désactivé par défaut. Pour plus d’informations sur l’activation des avertissements désactivés par défaut, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4062 et montre comment la corriger :

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur (niveau 4) C4061](compiler-warning-level-4-c4061.md)
