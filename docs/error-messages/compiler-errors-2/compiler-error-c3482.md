---
description: 'En savoir plus sur : erreur du compilateur C3482'
title: Erreur du compilateur C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 752ce53b590ef5c10c25e0d0e850c7c4cc2776bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315697"
---
# <a name="compiler-error-c3482"></a>Erreur du compilateur C3482

'this' peut uniquement être utilisé en tant que capture lambda dans une fonction membre non statique

Vous ne pouvez pas passer **`this`** à la liste de capture d’une expression lambda déclarée dans une méthode statique ou une fonction globale.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Convertissez la fonction englobante en méthode non statique.

- Supprimez le **`this`** pointeur de la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3482 :

```cpp
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
