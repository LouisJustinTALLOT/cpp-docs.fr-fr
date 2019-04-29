---
title: Avertissement du compilateur (niveau 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 556c6e0963fc41d76cd123373cc4cd85edc66962
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384138"
---
# <a name="compiler-warning-level-1-c4964"></a>Avertissement du compilateur (niveau 1) C4964

Aucune option d’optimisation a été spécifiée ; informations de profil ne seront pas collectées.

[/GL](../../build/reference/gl-whole-program-optimization.md) et [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) ont été spécifiées, mais aucune optimisation n’ont été demandés, donc aucun fichier .pgc n’est générée et, par conséquent, aucune optimisation guidée par profil ne sera possible.

Si vous souhaitez que les fichiers .pgc doit être généré lorsque vous exécutez votre application, spécifiez l’une de la [/O](../../build/reference/o-options-optimize-code.md) options du compilateur.

L’exemple suivant génère l’erreur C4964 :

```
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```