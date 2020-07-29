---
title: Erreur du compilateur C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 0463f6de51e324bd02c8b766fd39909ee2803ecd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212577"
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
