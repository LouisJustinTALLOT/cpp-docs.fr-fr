---
title: Erreur du compilateur C2160 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2160
dev_langs:
- C++
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e823d841eabb4494d549721320f8f29d5cd8774
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111483"
---
# <a name="compiler-error-c2160"></a>Erreur du compilateur C2160

'##' ne peut se trouver au début de la définition d'une macro

La définition d’une macro a commencé par un opérateur de collage de jeton (##).

L’exemple suivant génère l’erreur C2160 :

```
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```