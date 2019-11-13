---
title: Avertissement du compilateur (niveau 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 2a75a1b7d3738794046ac697113c3c746bb6fcff
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052249"
---
# <a name="compiler-warning-level-1-c4964"></a>Avertissement du compilateur (niveau 1) C4964

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