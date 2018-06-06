---
title: __clrcall | Documents Microsoft
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
ms.openlocfilehash: 4012eac44f376ccdeeb57227e562c672f6ba7ffe
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704579"
---
# <a name="clrcall"></a>__clrcall

**Section spécifique à Microsoft**

Spécifie qu'une fonction peut uniquement être appelée à partir du code managé.  Utilisez `__clrcall` pour toutes les fonctions virtuelles qui seront uniquement appelées à partir du code managé. Toutefois, cette convention d’appel ne peut pas être utilisée pour les fonctions qui sont appelées à partir du code natif.

Utilisez `__clrcall` pour améliorer les performances lors d'un appel à partir d'une fonction managée à une fonction managée virtuelle ou à partir de la fonction managée à la fonction managée via le pointeur.

Les points d'entrée sont des fonctions séparées et générées par le compilateur. Si une fonction a des points d'entrée natifs et managés, l'un d'eux est la fonction réelle avec l'implémentation de fonction. L'autre fonction est une fonction séparée (une conversion de code) qui appelle la fonction réelle et qui laisse le Common Langage Runtime effectuer PInvoke. En marquant une fonction comme `__clrcall`, vous indiquez que l'implémentation de fonction doit être MSIL et que la fonction de point d'entrée native ne sera pas générée.

Au moment d'acquérir l'adresse d'une fonction native si `__clrcall` n'est pas spécifié, le compilateur utilise le point d'entrée natif. `__clrcall` indique que la fonction est gérée et qu'il n'est pas nécessaire de passer par la transition entre le code managé et le code natif. Dans ce cas, le compilateur utilise le point d'entrée managé.

Lorsque **/CLR** (pas **/CLR : pure** ou **/CLR : safe**) est utilisé et `__clrcall` est ne pas utilisé, la prise d’adresse d’une fonction toujours retourne l’adresse de l’entrée native fonction de point. Lorsque `__clrcall` est utilisé, la fonction de point d'entrée native n'est pas créée, vous obtenez donc l'adresse de la fonction managée, pas une fonction de conversion de code de point d'entrée. Pour plus d’informations, consultez [Double médiateur](../dotnet/double-thunking-cpp.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

[/CLR (Compilation pour le common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) implique que toutes les fonctions et les pointeurs de fonction sont `__clrcall` et le compilateur ne permettra pas d’une fonction à l’intérieur du module à quoi que ce soit marquer autre que `__clrcall`. Lorsque **/CLR : pure** est utilisé, `__clrcall` peut être spécifié uniquement sur les pointeurs de fonction et les déclarations externes.

Vous pouvez appeler directement `__clrcall` fonctions à partir de code C++ existant qui a été compilé à l’aide de **/CLR** tant que cette fonction a une implémentation MSIL. `__clrcall` les fonctions ne peut pas être appelées directement à partir de fonctions qui ont le code asm incorporé et appellent des intrinsèques spécifiques UC, par exemple, même si ces fonctions sont compilées avec **/CLR**.

Des pointeurs fonction `__clrcall` sont uniquement destinés à être utilisés dans le domaine d'application dans lequel ils ont été créés.  Au lieu de passer des pointeurs fonction `__clrcall` entre des domaines d'application, utilisez <xref:System.CrossAppDomainDelegate>. Pour plus d’informations, consultez [domaines d’Application et Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Exemple

Notez que lorsqu'une fonction est déclarée avec `__clrcall`, le code sera généré lorsque nécessaire ; par exemple, lorsque la fonction est appelée.

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

- [Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)
- [Mots clés](../cpp/keywords-cpp.md)
