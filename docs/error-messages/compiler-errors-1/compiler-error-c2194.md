---
title: Erreur du compilateur C2194
ms.date: 11/04/2016
f1_keywords:
- C2194
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
ms.openlocfilehash: 6059b54c0b30bd11e1c8bc6f3779f4739d344ff7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174573"
---
# <a name="compiler-error-c2194"></a>Erreur du compilateur C2194

'identificateur' : segment texte

Le `data_seg` pragma utilise un nom de segment utilisé avec `code_seg`.

L’exemple suivant génère l’erreur C2194 :

```
// C2194.cpp
// compile with: /c
#pragma code_seg("MYCODE")
#pragma data_seg("MYCODE")   // C2194
#pragma data_seg("MYCODE2")   // OK
```