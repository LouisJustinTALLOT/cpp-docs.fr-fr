---
title: Erreur du compilateur C3484 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a79574f85d05c6b1ac32416509ba1f8c05e26b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019184"
---
# <a name="compiler-error-c3484"></a>Erreur du compilateur C3484

'->' attendu avant le type de retour

Vous devez indiquer `->` avant le type de retour d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Indiquez `->` avant le type de retour.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3484 :

```
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Exemple

L’exemple suivant résout l’erreur C3484 en fournissant `->` avant le type de retour de l’expression lambda :

```
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)