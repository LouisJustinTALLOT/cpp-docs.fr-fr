---
title: Erreur du compilateur C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: fd8909b664f739afa1ab1208be0984b8f410154d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468636"
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