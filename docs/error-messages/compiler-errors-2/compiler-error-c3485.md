---
title: Erreur du compilateur C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027554"
---
# <a name="compiler-error-c3485"></a>Erreur du compilateur C3485

une définition d'expression lambda ne peut pas contenir de qualificateurs cv

Vous ne pouvez pas utiliser un qualificateur `const` ou `volatile` dans le cadre de la définition d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez le qualificateur `const` ou `volatile` de la définition de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3485, car il utilise le qualificateur `const` dans le cadre de la définition d’une expression lambda :

```
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)