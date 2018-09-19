---
title: Erreur du compilateur C2745 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2745
dev_langs:
- C++
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d08e89fe3dbcfbff8c947b432bda94e9ac15ef99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099862"
---
# <a name="compiler-error-c2745"></a>Erreur du compilateur C2745

'jeton' : ce jeton ne peut pas être converti en un identificateur

Identificateurs doivent être constitués de caractères autorisés.

L’exemple suivant génère l’erreur C2745 :

```
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```