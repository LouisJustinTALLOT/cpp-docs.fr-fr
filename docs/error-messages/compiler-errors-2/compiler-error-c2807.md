---
title: Erreur du compilateur C2807 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2807
dev_langs:
- C++
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a0f1627e19ad3368ad99559b6b576d165347643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110534"
---
# <a name="compiler-error-c2807"></a>Erreur du compilateur C2807

le second paramètre formel du suffixe 'operator opérateur' doit être 'int'

Le deuxième paramètre à un opérateur suffixé a un type incorrect.

L’exemple suivant génère l’erreur C2807 :

```
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```