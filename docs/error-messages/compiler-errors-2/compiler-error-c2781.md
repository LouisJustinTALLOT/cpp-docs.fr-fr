---
title: Erreur du compilateur C2781 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2781
dev_langs:
- C++
helpviewer_keywords:
- C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3662a1be167f6a443606139ff49daebc5c923eec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095480"
---
# <a name="compiler-error-c2781"></a>Erreur du compilateur C2781

'déclaration' : attend au moins argument value1 - valeur2 fournis

Un modèle de fonction avec une liste de paramètres de variable a trop peu d’arguments.

L’exemple suivant génère l’erreur C2781 :

```
// C2781.cpp
template<typename T>
void f(T, T, ...){}

int main() {
   f(1);   // C2781

   // try the following line instead
   f(1,1);
}
```