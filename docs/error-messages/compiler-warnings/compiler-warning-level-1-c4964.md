---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4964'
title: Avertissement du compilateur (niveau 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 102c04332bd40f6f1ae95cbd025c7400fc77dbf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327925"
---
# <a name="compiler-warning-level-1-c4964"></a>Avertissement du compilateur (niveau 1) C4964

Aucune option d’optimisation n’a été spécifiée ; les informations de profil ne seront pas collectées

[/GL](../../build/reference/gl-whole-program-optimization.md) et [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) ont été spécifiés, mais aucune optimisation n’a été demandée, donc aucun fichier. PGC ne sera généré et, par conséquent, aucune optimisation guidée par profil n’est possible.

Si vous souhaitez que les fichiers. PGC soient générés lorsque vous exécutez votre application, spécifiez l’une des options du compilateur [/o](../../build/reference/o-options-optimize-code.md) .

L’exemple suivant génère l’C4964 :

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```
