---
title: Compilateur avertissement (niveau 1) C4806 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b580500c3887fe60b7864280ad5ca1804752f2ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062603"
---
# <a name="compiler-warning-level-1-c4806"></a>Avertissement du compilateur (niveau 1) C4806

'opération' : opération risquée : aucune valeur de type 'type' promue en type 'type' ne peut être égale à la constante donnée

Ce message fournit un avertissement contre le code tel que `b == 3`, où `b` est de type `bool`. Les règles de promotion entraînent la promotion de `bool` en `int`. Cela est légal, mais ne peut jamais être **true**. L’exemple suivant génère l’erreur C4806 :

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```