---
title: Erreur du compilateur C2898 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2898
dev_langs:
- C++
helpviewer_keywords:
- C2898
ms.assetid: 68466e11-2541-4f6b-b772-13a642f30dfb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b34eaf73840d4c156299128209cd5c519155473
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110040"
---
# <a name="compiler-error-c2898"></a>Erreur du compilateur C2898

'déclaration' : les modèles de fonction membre ne peut pas être virtuels

L’exemple suivant génère l’erreur C2898 :

```
// C2898.cpp
// compile with: /c
class X {
public:
   template<typename T> virtual void f(T t) {}   // C2898
};
```