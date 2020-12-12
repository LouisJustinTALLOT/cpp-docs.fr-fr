---
description: 'En savoir plus sur : erreur du compilateur C2657'
title: Erreur du compilateur C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: dfec399c4b65615310263aa58db145b87c42594d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286070"
---
# <a name="compiler-error-c2657"></a>Erreur du compilateur C2657

'Class ::* 'trouvé au début d’une instruction (n’auriez-vous pas oublié de spécifier un type ?)

La ligne commence par un identificateur pointeur vers membre.

Cette erreur peut être causée par un spécificateur de type manquant dans la déclaration d’un pointeur vers un membre.

L’exemple suivant génère l’C2657 :

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```
