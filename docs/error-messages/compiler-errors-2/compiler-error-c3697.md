---
title: Erreur du compilateur C3697 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3697
dev_langs:
- C++
helpviewer_keywords:
- C3697
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb5755cc737c0cc5524cb6abd980b70d08b6cf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050656"
---
# <a name="compiler-error-c3697"></a>Erreur du compilateur C3697

'identificateur' : Impossible d’utiliser ce qualificateur sur ' ^'

Le handle de suivi (^) a été appliqué à un qualificateur pour lequel il n’a pas été conçu.

L’exemple suivant génère l’erreur C3697 :

```
// C3697.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^__restrict s;   // C3697
   String ^ s2;   // OK
}
```