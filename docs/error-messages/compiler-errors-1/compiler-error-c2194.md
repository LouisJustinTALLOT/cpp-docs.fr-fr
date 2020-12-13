---
description: 'En savoir plus sur : erreur du compilateur C2194'
title: Erreur du compilateur C2194
ms.date: 11/04/2016
f1_keywords:
- C2194
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
ms.openlocfilehash: fefdfbc434dce1347ff4a46a56040219f64feb47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337636"
---
# <a name="compiler-error-c2194"></a>Erreur du compilateur C2194

'identificateur' : segment de texte

Le `data_seg` pragma utilise un nom de segment utilisé avec `code_seg` .

L’exemple suivant génère l’C2194 :

```cpp
// C2194.cpp
// compile with: /c
#pragma code_seg("MYCODE")
#pragma data_seg("MYCODE")   // C2194
#pragma data_seg("MYCODE2")   // OK
```
