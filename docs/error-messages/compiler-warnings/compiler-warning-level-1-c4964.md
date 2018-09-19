---
title: Compilateur avertissement (niveau 1) C4964 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1644e4603bae36ec9d407294dea78a27e60539
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086666"
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