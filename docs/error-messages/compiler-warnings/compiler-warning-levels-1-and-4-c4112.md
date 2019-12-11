---
title: Avertissement du compilateur (niveaux 1 et 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: f614373e1b96de2c8167d7981c0a87a4e1c58435
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991227"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Avertissement du compilateur (niveaux 1 et 4) C4112

\#ligne requiert un entier compris entre 1 et nombre

La directive [#line](../../preprocessor/hash-line-directive-c-cpp.md) spécifie un paramètre entier qui se trouve en dehors de la plage autorisée.

Si le paramètre spécifié est inférieur à 1, le compteur de lignes est réinitialisé à 1. Si le paramètre spécifié est supérieur à *nombre*, qui est la limite définie par le compilateur, le compteur de lignes est inchangé. Il s’agit d'un avertissement de niveau 1 sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) et un avertissement de niveau 4 avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

L’exemple suivant génère l’avertissement C4112 :

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```
