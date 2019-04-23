---
title: Erreur du compilateur C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 463e210e5a1ac5eb6d197062ed8921f9bbae4ad2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037881"
---
# <a name="compiler-error-c3498"></a>Erreur du compilateur C3498

'var' : vous ne pouvez pas capturer une variable qui a géré ou un WinRTtype

Vous ne pouvez pas capturer une variable dotée d'un type managé ou d'un type Windows Runtime dans une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Transmettez la variable managée ou de Windows Runtime dans la liste des paramètres de l'expression lambda.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3498, car une variable dotée d’un type managé figure dans la liste de capture d’une expression lambda :

```
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>Exemple

L’exemple suivant résout l’erreur C3498 en transmettant la variable managée `s` à la liste des paramètres de l’expression lambda :

```
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)