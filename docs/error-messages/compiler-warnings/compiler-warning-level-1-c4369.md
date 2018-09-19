---
title: Compilateur avertissement (niveau 1) C4369 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c8b292717168f7f6ead676528a5b7769b7c8ec4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024149"
---
# <a name="compiler-warning-level-1-c4369"></a>Avertissement du compilateur (niveau 1) C4369

'énumérateur' : valeur de l’énumérateur 'value' ne peut pas être représentée comme 'type', la valeur est 'nouvelle_valeur'

Un énumérateur a été calculé est supérieure à la plus grande valeur pour le type sous-jacent spécifié.  Cela a provoqué un dépassement de capacité et le compilateur a la valeur de l’énumérateur à la plus petite valeur possible pour le type encapsulé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4369 :.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```