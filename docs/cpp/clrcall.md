---
title: __clrcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __clrcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9631ac9beb0e6263ac1cf7e60e11e498aa4c7667
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019755"
---
# <a name="clrcall"></a>__clrcall

**Section spécifique à Microsoft**

Spécifie qu'une fonction peut uniquement être appelée à partir du code managé.  Utilisez **__clrcall** pour toutes les fonctions virtuelles qui seront appelées uniquement à partir du code managé. Toutefois, cette convention d’appel ne peut pas être utilisée pour les fonctions qui sont appelées à partir du code natif.

Utilisez **__clrcall** pour améliorer les performances lors de l’appel d’une fonction managée à une fonction managée virtuelle ou à partir de la fonction managée à la fonction managée via le pointeur.

Les points d'entrée sont des fonctions séparées et générées par le compilateur. Si une fonction a des points d'entrée natifs et managés, l'un d'eux est la fonction réelle avec l'implémentation de fonction. L'autre fonction est une fonction séparée (une conversion de code) qui appelle la fonction réelle et qui laisse le Common Langage Runtime effectuer PInvoke. En marquant une fonction en tant que **__clrcall**, vous indiquez l’implémentation de fonction doit être MSIL et que la fonction de point d’entrée natif n’est pas générée.

Lorsque vous prenez l’adresse d’une fonction native si **__clrcall** n’est pas spécifié, le compilateur utilise le point d’entrée natif. **__clrcall** indique que la fonction est gérée et il est inutile d’accéder à la transition à partir de gérés natif. Dans ce cas, le compilateur utilise le point d'entrée managé.

Lorsque `/clr` (pas `/clr:pure` ou `/clr:safe`) est utilisé et **__clrcall** est ne pas utilisé, en prenant toujours de l’adresse d’une fonction retourne l’adresse de la fonction de point d’entrée natif. Lorsque **__clrcall** est utilisé, la fonction de point d’entrée natif n'est pas créée, vous obtenez l’adresse de la fonction managée, pas une fonction thunk de point d’entrée. Pour plus d’informations, consultez [Double médiateur](../dotnet/double-thunking-cpp.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

[/CLR (Compilation pour le common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) implique que toutes les fonctions et les pointeurs de fonction sont **__clrcall** et le compilateur ne permet pas d’une fonction à l’intérieur du module d’être marquée comme autre chose que **__clrcall**. Lorsque **/CLR : pure** est utilisé, **__clrcall** peut être spécifiée qu’avec des pointeurs de fonction et les déclarations externes.

Vous pouvez appeler directement **__clrcall** fonctions à partir de code C++ existant qui a été compilé à l’aide de **/CLR** tant que cette fonction a une implémentation MSIL. **__clrcall** fonctions ne peut pas être appelées directement à partir de fonctions qui ont des code asm incorporé et appellent des intrinsèques spécifiques UC, par exemple, même si ces fonctions sont compilées avec `/clr`.

**__clrcall** des pointeurs de fonction sont uniquement destinés à être utilisés dans le domaine d’application dans lequel ils ont été créés.  Au lieu de passer **__clrcall** des pointeurs de fonction entre domaines d’application, utilisez <xref:System.CrossAppDomainDelegate>. Pour plus d’informations, consultez [domaines d’Application et Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Exemple

Notez que lorsqu’une fonction est déclarée avec **__clrcall**, le code sera généré lorsque nécessaire ; par exemple, lorsque la fonction est appelée.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>Exemple

L'exemple suivant montre que vous pouvez définir un pointeur fonction, de sorte que vous indiquez que le pointeur fonction sera uniquement appelé à partir du code managé. Cela permet au compilateur d'appeler directement la fonction managée et d'éviter le point d'entrée natif (double problème de conversion de code).

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
