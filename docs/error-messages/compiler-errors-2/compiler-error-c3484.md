---
title: Erreur du compilateur C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c9895a3e5a8ae7e941fccde2da85fedfb3d2c6dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743118"
---
# <a name="compiler-error-c3484"></a>Erreur du compilateur C3484

'->' attendu avant le type de retour

Vous devez indiquer `->` avant le type de retour d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Indiquez `->` avant le type de retour.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3484 :

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Exemple

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
