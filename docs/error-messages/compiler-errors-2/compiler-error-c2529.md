---
title: Erreur du compilateur C2529
ms.date: 11/04/2016
f1_keywords:
- C2529
helpviewer_keywords:
- C2529
ms.assetid: 73a99e55-b91e-488d-9b72-cc80faaeb436
ms.openlocfilehash: f5a10131fe03bd98078e87f71d07bf02c51d34f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760411"
---
# <a name="compiler-error-c2529"></a>Erreur du compilateur C2529

'nom' : la référence à une référence n’est pas conforme

Cette erreur peut être résolue à l’aide de la syntaxe du pointeur et de la déclaration d’une référence à un pointeur.

L’exemple suivant génère l’C2529 :

```cpp
// C2529.cpp
// compile with: /c
int i;
int &ri = i;
int &(&rri) = ri;   // C2529
```
