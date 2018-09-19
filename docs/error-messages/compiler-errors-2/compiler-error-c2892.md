---
title: Erreur du compilateur C2892 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2892
dev_langs:
- C++
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04efc10f6613029b2a6e4947dc202555f0d53501
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097241"
---
# <a name="compiler-error-c2892"></a>Erreur du compilateur C2892

classe locale ne doit pas avoir de modèles membres

Fonctions membres basé sur un modèle ne sont pas valides dans une classe qui est définie dans une fonction.

L’exemple suivant génère l’erreur C2892 :

```
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```