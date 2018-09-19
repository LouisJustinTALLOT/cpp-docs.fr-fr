---
title: Erreur du compilateur C3485 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3eee53f23aa2cdc958b63faed11ead302f4b1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060744"
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