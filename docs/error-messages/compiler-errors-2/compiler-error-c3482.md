---
title: Erreur du compilateur C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 6ff269d719dd354932ef79946ae99a9b60490199
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039422"
---
# <a name="compiler-error-c3482"></a>Erreur du compilateur C3482

'this' peut uniquement être utilisé en tant que capture lambda dans une fonction membre non statique

Vous ne pouvez pas passer `this` à la liste de capture d’une expression lambda qui est déclarée dans une méthode statique ou une fonction globale.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Convertissez la fonction englobante en méthode non statique.

- Vous pouvez aussi supprimer le pointeur `this` de la liste de capture de l’expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3482 :

```
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