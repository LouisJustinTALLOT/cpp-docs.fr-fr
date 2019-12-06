---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857604"
---
# <a name="__clrcall"></a>__clrcall

Spécifie qu'une fonction peut uniquement être appelée à partir du code managé.  Utilisez **__clrcall** pour toutes les fonctions virtuelles qui seront appelées uniquement à partir du code managé. Toutefois, cette convention d’appel ne peut pas être utilisée pour les fonctions qui sont appelées à partir du code natif. Le modificateur de **__clrcall** est spécifique à Microsoft.

Utilisez **__clrcall** pour améliorer les performances lors de l’appel d’une fonction managée à une fonction managée virtuelle ou d’une fonction managée à une fonction managée à l’aide d’un pointeur.

Les points d'entrée sont des fonctions séparées et générées par le compilateur. Si une fonction a des points d'entrée natifs et managés, l'un d'eux est la fonction réelle avec l'implémentation de fonction. L'autre fonction est une fonction séparée (une conversion de code) qui appelle la fonction réelle et qui laisse le Common Langage Runtime effectuer PInvoke. Quand vous marquez une fonction comme **__clrcall**, vous indiquez que l’implémentation de fonction doit être MSIL et que la fonction de point d’entrée Native ne sera pas générée.

Lors de l’utilisation de l’adresse d’une fonction native si **__clrcall** n’est pas spécifié, le compilateur utilise le point d’entrée natif. **__clrcall** indique que la fonction est managée et qu’il n’est pas nécessaire de passer par la transition de managé à natif. Dans ce cas, le compilateur utilise le point d'entrée managé.

Lorsque `/clr` (non `/clr:pure` ou `/clr:safe`) est utilisé et **__clrcall** n’est pas utilisé, l’utilisation de l’adresse d’une fonction retourne toujours l’adresse de la fonction de point d’entrée native. Lorsque **__clrcall** est utilisé, la fonction de point d’entrée Native n’est pas créée. vous recevez donc l’adresse de la fonction managée, et non une fonction thunk de point d’entrée. Pour plus d’informations, consultez [double médiateur](../dotnet/double-thunking-cpp.md). Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

[/clr (compilation du Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) implique que toutes les fonctions et les pointeurs de fonction sont **__clrcall** et que le compilateur n’autorise pas la marquage d’une fonction à l’intérieur du module de ligne de fonction autre que **__clrcall**. Quand **/clr : pure** est utilisé, **__clrcall** peut être spécifié uniquement sur les pointeurs de fonction et les déclarations externes.

Vous pouvez appeler directement des fonctions **__clrcall** à C++ partir de code existant qui a été compilé à l’aide de **/CLR** tant que cette fonction a une implémentation MSIL. les fonctions **__clrcall** ne peuvent pas être appelées directement à partir de fonctions qui ont un ASM inline et appellent des intrinsèques spécifiques au processeur, par exemple, même si ces fonctions sont compilées avec `/clr`.

**__clrcall** pointeurs de fonction sont uniquement destinés à être utilisés dans le domaine d’application dans lequel ils ont été créés.  Au lieu de passer des pointeurs de fonction **__clrcall** à travers des domaines d’application, utilisez <xref:System.CrossAppDomainDelegate>. Pour plus d’informations, consultez [domaines d’application C++et visuels ](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Exemple

Notez que lorsqu’une fonction est déclarée avec **__clrcall**, du code est généré quand cela est nécessaire ; par exemple, lorsque la fonction est appelée.

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
