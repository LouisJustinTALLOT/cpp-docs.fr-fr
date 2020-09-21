---
title: Erreur du compilateur C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 360fedc6cadf275704a790c257c42ac8bde7873d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742058"
---
# <a name="compiler-error-c3409"></a>Erreur du compilateur C3409

> bloc d’attributs vide non autorisé

## <a name="remarks"></a>Notes

Les crochets ont été interprétés par le compilateur comme un bloc d' [attributs](../../windows/attributes-alphabetical-reference.md) , mais aucun attribut n’a été trouvé.

Le compilateur peut générer cette erreur quand vous utilisez des crochets dans le cadre de la définition d’une expression lambda. Cette erreur se produit lorsque le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs. Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si les crochets font partie d’un bloc d’attributs :

   1. Fournissez un ou plusieurs attributs dans le bloc d’attributs.

   1. Supprimez le bloc d’attributs.

1. Si les crochets font partie d’une expression lambda, assurez-vous que l’expression lambda respecte les règles syntaxiques valides.

   Pour plus d’informations sur la syntaxe d’expression lambda, consultez [syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C3409.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

L’exemple suivant génère C3409, car une expression lambda utilise la **`mutable`** spécification, mais ne fournit pas de liste de paramètres. Le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Voir aussi

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)
