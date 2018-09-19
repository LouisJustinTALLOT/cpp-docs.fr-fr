---
title: Erreur du compilateur C2390 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de5a9af8f8aa04219f0a7d61162336745fd4bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098210"
---
# <a name="compiler-error-c2390"></a>Erreur du compilateur C2390

'identificateur' : classe de stockage incorrecte 'spécificateur'

La classe de stockage n’est pas valide pour l’identificateur de portée globale. La classe de stockage par défaut est utilisée à la place de la classe non valide.

Solutions possibles :

- Si l’identificateur est une fonction, déclarez-le avec `extern` stockage.

- Si l’identificateur est un paramètre formel ou une variable locale, déclarez-le à l’aide du stockage automatique.

- Si l’identificateur est une variable globale, déclarez-le sans classe de stockage (stockage automatique).

## <a name="example"></a>Exemple

- L’exemple suivant génère l’erreur C2390 :

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```