---
description: 'En savoir plus sur : code pur et vérifiable (C++/CLI)'
title: Code pur et vérifiable (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
ms.openlocfilehash: 64224f7f462b5e11e522648a5b64ec9d568dc53f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276762"
---
# <a name="pure-and-verifiable-code-ccli"></a>Code pur et vérifiable (C++/CLI)

Pour la programmation .NET, Visual C++ dans Visual Studio 2017 prend en charge la création d’assemblys mixtes à l’aide de l’option de compilateur [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) . Les options **/clr : pure** et **clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017. Si votre code doit être sécurisé ou vérifiable, nous vous recommandons de le porter vers C#.

## <a name="mixed-clr"></a>Mixte (/CLR)

Les assemblys mixtes (compilés avec **/CLR**) contiennent à la fois des parties non gérées et gérées, ce qui leur permet d’utiliser les fonctionnalités .net, mais qui contiennent toujours du code natif. Cela permet aux applications et aux composants d’être mis à jour pour utiliser les fonctionnalités .NET sans avoir à réécrire la totalité du projet. L’utilisation de Visual C++ pour mélanger du code managé et natif de cette manière est appelée l’interopérabilité C++. Pour plus d’informations, consultez [assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md) et [interopérabilité native et .net](../dotnet/native-and-dotnet-interoperability.md).

Les appels effectués à partir d’assemblys managés vers des DLL natives via P/Invoke se compilent, mais peuvent échouer au moment de l’exécution en fonction des paramètres de sécurité.

Il existe un scénario de codage qui passera le compilateur, mais cela entraînera un assembly non vérifiable : appel d’une fonction virtuelle via une instance d’objet à l’aide de l’opérateur de résolution de portée.  Par exemple : `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Voir aussi

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
