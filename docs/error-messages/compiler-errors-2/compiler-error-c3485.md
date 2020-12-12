---
description: 'En savoir plus sur : erreur du compilateur C3485'
title: Erreur du compilateur C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0b11eb4487a9b6deb611852dd11a8a1963dd961e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168382"
---
# <a name="compiler-error-c3485"></a>Erreur du compilateur C3485

une définition d'expression lambda ne peut pas contenir de qualificateurs cv

Vous ne pouvez pas utiliser un **`const`** **`volatile`** qualificateur ou dans le cadre de la définition d’une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez **`const`** le **`volatile`** qualificateur ou de la définition de votre expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère C3485, car il utilise le **`const`** qualificateur dans le cadre de la définition d’une expression lambda :

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
