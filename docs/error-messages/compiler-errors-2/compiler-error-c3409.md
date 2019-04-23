---
title: Erreur du compilateur C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 24f107e0c1f74f95afc521c8a4c888a26a35c13a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033759"
---
# <a name="compiler-error-c3409"></a>Erreur du compilateur C3409

> bloc d’attributs vide n’est pas autorisée.

## <a name="remarks"></a>Notes

Les crochets étaient interprétés par le compilateur comme un [attribut](../../windows/attributes-alphabetical-reference.md) bloc, mais aucun attribut n’a été trouvé.

Le compilateur peut générer cette erreur lorsque vous utilisez des crochets dans le cadre de la définition d’une expression lambda. Cette erreur se produit lorsque le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si les crochets font partie d’un bloc d’attributs :

   1. Fournir un ou plusieurs attributs dans le bloc d’attributs.

   1. Supprimez le bloc d’attributs.

1. Si les crochets font partie d’une expression lambda, assurez-vous que l’expression lambda suit les règles de syntaxe valide.

   Pour plus d’informations sur la syntaxe d’expression lambda, consultez [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3409.

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

## <a name="example"></a>Exemple

L’exemple suivant génère C3409, car une expression lambda utilise le `mutable` spécification, mais ne fournit ne pas une liste de paramètres. Le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs.

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