---
title: Erreur du compilateur C3409
ms.date: 11/04/2016
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 2a677da40b64a19c4d2a27436344eec7adb80c14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600887"
---
# <a name="compiler-error-c3409"></a>Erreur du compilateur C3409

bloc d’attributs vide n’est pas autorisée.

Les crochets étaient interprétés par le compilateur comme un [attribut](../../windows/cpp-attributes-reference.md) bloc, mais aucun attribut n’a été trouvé.

Le compilateur peut générer cette erreur lorsque vous utilisez des crochets dans le cadre de la définition d’une expression lambda. Cette erreur se produit lorsque le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Si les crochets font partie d’un bloc d’attributs :

   1. Fournir un ou plusieurs attributs dans le bloc d’attributs.

   1. Supprimez le bloc d’attributs.

1. Si les crochets font partie d’une expression lambda :

   1. Assurez-vous que l’expression lambda suit les règles de syntaxe valide.

         Pour plus d’informations sur la syntaxe d’expression lambda, consultez [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).

    2.

## <a name="example"></a>Exemple

L’exemple suivant génère C3409.

```
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

```
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Voir aussi

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)