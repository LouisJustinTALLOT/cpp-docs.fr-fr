---
description: 'En savoir plus sur : erreur du compilateur C3484'
title: Erreur du compilateur C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: 6d3e72ef89ad33333c840b549cfc5c7c40495130
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315684"
---
# <a name="compiler-error-c3484"></a>Erreur du compilateur C3484

'->' attendu avant le type de retour

Vous devez indiquer `->` avant le type de retour d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Indiquez `->` avant le type de retour.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3484 :

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

L’exemple suivant résout l’erreur C3484 en fournissant `->` avant le type de retour de l’expression lambda :

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
