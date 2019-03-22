---
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
ms.openlocfilehash: b91918d526d83d4cf47436d02b7c67038576bafb
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356177"
---
# <a name="managed-types-ccli"></a>Types managés (C++/CLI)

Visual C++ permet d’accéder aux fonctionnalités .NET via des types managés, qui prennent en charge les fonctionnalités du common language runtime et sont soumis aux avantages et restrictions du runtime.

## <a name="main_functions"></a> Types managés et fonction main

Lorsque vous écrivez une application à l’aide **/CLR**, les arguments de la **main()** fonction ne peut pas être d’un type managé.

Est un exemple d’une signature correcte :

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> Équivalents .NET framework des types natifs C++

Le tableau suivant présente les mots clés des types intégrés Visual C++, qui sont des alias des types prédéfinis dans le **système** espace de noms.

|Type de Visual C++|Type .NET Framework|
|-----------------------|-------------------------|
|**void**|<xref:System.Void?displayProperty=nameWithType>|
|**bool**|<xref:System.Boolean?displayProperty=nameWithType>|
|**char signé** |<xref:System.SByte?displayProperty=nameWithType>|
|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|
|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|
|**court** et **signés short**|<xref:System.Int16?displayProperty=nameWithType>|
|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|
|**int**, **type signed int**, **long**, et **long signé**|<xref:System.Int32?displayProperty=nameWithType>|
|**unsigned int** et **long non signé**|<xref:System.UInt32?displayProperty=nameWithType>|
|**__int64** et **signé __int64**|<xref:System.Int64?displayProperty=nameWithType>|
|**unsigned __int64**|<xref:System.UInt64?displayProperty=nameWithType>|
|**float**|<xref:System.Single?displayProperty=nameWithType>|
|**Double** et **long double**|<xref:System.Double?displayProperty=nameWithType>|

Pour plus d’informations sur l’option de compilateur par défaut non signé ou signé **char**, consultez [/J (type de caractère par défaut n’est pas signé)](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version_issues"></a> Problèmes de version pour les Types valeur imbriqués dans les Types natifs

Envisagez un composant d’assembly signé (nom fort) utilisé pour générer un assembly client. Le composant contient un type valeur qui est utilisé dans le client comme type pour un membre d’une union native, une classe ou un tableau. Si une version future du composant modifie la taille ou la disposition du type valeur, le client doit être recompilé.

Créez un fichier de clé avec [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).

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

### <a name="output"></a>Sortie

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>Commentaires

Toutefois, si vous ajoutez un autre membre `struct S` dans nested_value_types.cpp, (par exemple, `double d;`) et recompiler le composant sans recompiler le client, le résultat est une exception non gérée (de type <xref:System.IO.FileLoadException?displayProperty=fullName>).

## <a name="test_equality"></a> Guide pratique pour Test d’égalité

Dans l’exemple suivant, un test d’égalité qui utilise les Extensions managées pour C++ est basé sur quoi les descripteurs de référence.

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

Le langage intermédiaire pour ce programme montre que la valeur de retour est implémentée à l’aide d’un appel à op_Equality.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a> Guide pratique pour Diagnostiquer et résoudre les problèmes de compatibilité d’Assembly

Cette rubrique explique ce qui peut se produire lorsque la version d’un assembly référencé au moment de la compilation ne correspond pas à la version de l’assembly référencé lors de l’exécution et comment éviter le problème.

Lorsqu’un assembly est compilé, les autres assemblys peuvent être référencés avec la `#using` syntaxe. Lors de la compilation, ces assemblys sont accessibles par le compilateur. Informations à partir de ces assemblys sont utilisées pour prendre des décisions d’optimisation.

Toutefois, si l’assembly référencé est modifié et recompilé, et vous ne pas recompilez l’assembly de référence qui en dépend, les assemblys peut ne pas toujours être compatible. Les décisions d’optimisation qui étaient valides à tout d’abord peut-être pas correctes par rapport à la nouvelle version de l’assembly. Diverses erreurs d’exécution peuvent se produire en raison de ces incompatibilités. Il n’existe aucune exception spécifique qui est générée dans ce cas. La façon de que l’échec est consigné lors de l’exécution dépend de la nature de la modification de code qui a provoqué le problème.

Ces erreurs ne doivent pas être un problème dans votre code de production final, que l’application entière est reconstruite pour la version publiée de votre produit. Les assemblys qui sont proposées au public doivent être marqués avec un numéro de version officielle afin de vous assurer que ces problèmes sont évités. Pour plus d’informations, consultez [Versioning des assemblys](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostiquer et résoudre une erreur d’incompatibilité

1. Si vous rencontrez des exceptions runtime ou autres conditions d’erreur qui se produisent dans le code qui référence un autre assembly et que vous disposez d’aucun autre cause identifiée, vous pourrez être confronté à un assembly obsolète.

1. Tout d’abord, isoler et reproduire l’exception ou une autre condition d’erreur. Un problème qui se produit en raison d’une exception obsolète doit être reproductible.

1. Vérifiez l’horodatage de tous les assemblys référencés dans votre application.

1. Si les horodateurs de tous les assemblys référencés par la suite à l’horodateur de la dernière compilation de votre application, votre application est obsolète. Si cela se produit, recompiler votre application avec l’assembly le plus récent et apportez les modifications de code requis.

1. Réexécutez l’application, effectuez les étapes pour reproduire le problème et vérifiez que l’exception ne se produit pas.

### <a name="example"></a>Exemple

Le programme suivant illustre le problème en réduisant l’accessibilité d’une méthode et tente d’accéder à cette méthode dans un autre assembly sans avoir à recompiler. Essayez de compiler `changeaccess.cpp` première. Il s’agit de l’assembly référencé qui changera. Ensuite, compilez `referencing.cpp`. La compilation réussit. À présent, réduire l’accessibilité de la méthode appelée. Recompilez `changeaccess.cpp` avec l’indicateur `/DCHANGE_ACCESS`. Cela rend la méthode protégée, plutôt que privé, il peut donc plus être appelée légalement. Sans avoir à recompiler `referencing.exe`, réexécutez l’application. Une exception <xref:System.MethodAccessException> entraîne.

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

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interopérabilité avec d’autres langages .NET (C++-CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Types managés (C++-CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[Directive #using](../preprocessor/hash-using-directive-cpp.md)
