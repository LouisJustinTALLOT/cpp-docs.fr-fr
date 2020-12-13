---
description: 'En savoir plus sur : types managés (C++/CLI)'
title: Types managés (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: ccf126152216cfddb9a78cb5abc608f23cc3ba80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344456"
---
# <a name="managed-types-ccli"></a>Types managés (C++/CLI)

Visual C++ permet d’accéder aux fonctionnalités .NET par le biais de types managés, qui assurent la prise en charge des fonctionnalités du common language runtime et sont soumis aux avantages et aux restrictions du Runtime.

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a> Types managés et fonction main

Lors de l’écriture d’une application à l’aide **`/clr`** de, les arguments de la fonction **main ()** ne peuvent pas être d’un type managé.

Voici un exemple de signature correcte :

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a> .NET Framework équivalents aux types natifs C++

Le tableau suivant présente les mots clés des types de Visual C++ intégrés, qui sont des alias de types prédéfinis dans l’espace de noms **System** .

|Type de Visual C++|Type .NET Framework|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** les **`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**, **`signed int`** , **`long`** et **`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** les **`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** les **`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** les **`long double`**|<xref:System.Double?displayProperty=nameWithType>|

Pour plus d’informations sur l’option de compilateur pour la valeur par défaut **`signed char`** ou **`unsigned char`** , consultez [ `/J` (type par défaut : **`char`** **`unsigned`** )](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a> Problèmes de version pour les types valeur imbriqués dans les types natifs

Prenons l’exemple d’un composant d’assembly signé (nom fort) utilisé pour générer un assembly client. Le composant contient un type valeur qui est utilisé dans le client comme type pour un membre d’une Union native, une classe ou un tableau. Si une version ultérieure du composant modifie la taille ou la disposition du type de valeur, le client doit être recompilé.

Créez un KeyFile avec [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) ( `sn -k mykey.snk` ).

### <a name="example"></a>Exemple

L’exemple suivant est le composant.

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>Exemple

Cet exemple est le client :

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>Output

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>Commentaires

Toutefois, si vous ajoutez un autre membre à `struct S` dans nested_value_types. cpp, (par exemple, `double d;` ) et que vous recompilez le composant sans recompiler le client, le résultat est une exception non gérée (de type <xref:System.IO.FileLoadException?displayProperty=fullName> ).

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a> Comment : tester l’égalité

Dans l’exemple suivant, un test d’égalité qui utilise Extensions managées pour C++ est basé sur ce à quoi les handles font référence.

### <a name="example"></a>Exemple

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

Le langage intermédiaire de ce programme montre que la valeur de retour est implémentée à l’aide d’un appel à op_Equality.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a> Comment : diagnostiquer et résoudre les problèmes de compatibilité des assemblys

Cette rubrique explique ce qui peut se produire lorsque la version d’un assembly référencé au moment de la compilation ne correspond pas à la version de l’assembly référencée au moment de l’exécution et comment éviter le problème.

Lorsqu’un assembly est compilé, d’autres assemblys peuvent être référencés avec la `#using` syntaxe. Pendant la compilation, le compilateur accède à ces assemblys. Les informations de ces assemblys sont utilisées pour prendre des décisions d’optimisation.

Toutefois, si l’assembly référencé est modifié et recompilé, et si vous ne recompilez pas l’assembly de référence qui en dépend, les assemblys peuvent ne pas être encore compatibles. Les décisions d’optimisation valides au préalable peuvent ne pas être correctes par rapport à la nouvelle version de l’assembly. Diverses erreurs d’exécution peuvent se produire en raison de ces incompatibilités. Il n’existe aucune exception spécifique qui sera produite dans de tels cas. Le mode de signalement de l’échec au moment de l’exécution dépend de la nature de la modification de code qui a provoqué le problème.

Ces erreurs ne doivent pas être un problème dans le code de production final tant que l’application entière est reconstruite pour la version finale de votre produit. Les assemblys qui sont publiés dans le public doivent être signalés par un numéro de version officiel, ce qui garantit que ces problèmes sont évités. Pour plus d’informations, consultez [Versioning des assemblys](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostic et résolution d’une erreur d’incompatibilité

1. Si vous rencontrez des exceptions d’exécution ou d’autres conditions d’erreur qui se produisent dans le code qui fait référence à un autre assembly et n’ont aucune autre cause identifiée, vous pouvez être confronté à un assembly obsolète.

1. Tout d’abord, isolez et reproduisez l’exception ou une autre condition d’erreur. Un problème qui se produit en raison d’une exception obsolète doit être reproductible.

1. Vérifiez l’horodatage de tous les assemblys référencés dans votre application.

1. Si les horodateurs de tous les assemblys référencés sont postérieurs à l’horodateur de la dernière compilation de votre application, votre application est obsolète. Si cela se produit, recompilez votre application avec l’assembly le plus récent et apportez les modifications nécessaires au code.

1. Réexécutez l’application, effectuez les étapes qui reproduisent le problème et vérifiez que l’exception ne se produit pas.

### <a name="example"></a>Exemple

Le programme suivant illustre le problème en réduisant l’accessibilité d’une méthode et en tentant d’accéder à cette méthode dans un autre assembly sans recompilation. Essayez de compiler en `changeaccess.cpp` premier. Il s’agit de l’assembly référencé qui sera modifié. Ensuite, compilez `referencing.cpp` . La compilation a échoué. À présent, réduisez l’accessibilité de la méthode appelée. Recompilez `changeaccess.cpp` avec l’indicateur `/DCHANGE_ACCESS` . Cela rend la méthode protégée, plutôt que privée, afin qu’elle puisse être plus appelée légalement. Sans recompilation `referencing.exe` , réexécutez l’application. Une exception <xref:System.MethodAccessException> se produit.

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interopérabilité avec d’autres langages .NET (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Types managés (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using directive](../preprocessor/hash-using-directive-cpp.md)
