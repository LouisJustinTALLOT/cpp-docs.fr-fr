---
description: 'En savoir plus sur : erreur du compilateur C3498'
title: Erreur du compilateur C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: f4d4ccb67494eb2d2cab499c210d360415fa9779
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113099"
---
# <a name="compiler-error-c3498"></a>Erreur du compilateur C3498

'var' : vous ne pouvez pas capturer une variable qui a un managé ou un WinRTtype

Vous ne pouvez pas capturer une variable dotée d'un type managé ou d'un type Windows Runtime dans une expression lambda.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Transmettez la variable managée ou de Windows Runtime dans la liste des paramètres de l'expression lambda.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3498, car une variable dotée d’un type managé figure dans la liste de capture d’une expression lambda :

```cpp
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

L’exemple suivant résout l’erreur C3498 en transmettant la variable managée `s` à la liste des paramètres de l’expression lambda :

```cpp
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
