---
title: Erreur du compilateur C2118 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2118
dev_langs:
- C++
helpviewer_keywords:
- C2118
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91e79e396f707dc1462b17d9dd470527f199ad10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081635"
---
# <a name="compiler-error-c2118"></a>Erreur du compilateur C2118

indice négatif

La valeur définissant la taille du tableau est supérieure à la taille maximale du tableau ou inférieur à zéro.

L’exemple suivant génère l’erreur C2118 :

```
// C2118.cpp
int main() {
   int array1[-1];   // C2118
   int array2[3];   // OK
}
```