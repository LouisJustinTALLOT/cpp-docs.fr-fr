---
title: Erreur du compilateur C2431
ms.date: 11/04/2016
f1_keywords:
- C2431
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
ms.openlocfilehash: 6298748b341d58c5d931566f714530a4858e46ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608102"
---
# <a name="compiler-error-c2431"></a>Erreur du compilateur C2431

Registre d’index non conforme dans 'identificateur'

Le registre ESP est mis à l’échelle ou utilisé comme index et de Registre de base. FRÈRE de codage pour le x86 processeur n’autorise pas l’autre.

L’exemple suivant génère l’erreur C2431 :

```
// C2431.cpp
// processor: x86
int main() {
   _asm mov ax, [ESI + 2*ESP]   // C2431
   _asm mov ax, [esp + esp]   // C2431
}
```