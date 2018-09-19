---
title: Erreur du compilateur C2238 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2238
dev_langs:
- C++
helpviewer_keywords:
- C2238
ms.assetid: 3d53060c-d6b7-4603-b9cf-d7c65eb64cd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a1af9ef4f36198190d174d69ec825aa6e655616
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065983"
---
# <a name="compiler-error-c2238"></a>Erreur du compilateur C2238

jetons inattendus avant 'token'

Un jeton incorrect a été détecté.

L’exemple suivant génère l’erreur C2238 :

```
// C2238.cpp
// compile with: /c
class v {
virtual: int vvv;   // C2238
};
```