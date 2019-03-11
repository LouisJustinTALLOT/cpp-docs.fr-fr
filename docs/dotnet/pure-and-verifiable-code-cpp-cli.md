---
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
ms.openlocfilehash: 66f3b5a33791d20297cde6e6223ba65189a99682
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743829"
---
# <a name="pure-and-verifiable-code-ccli"></a>Code pur et vérifiable (C++ / c++ / CLI)

Pour la programmation .NET, Visual C++ dans Visual Studio 2017 prend en charge la création d’assemblys mixtes à l’aide de la [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le **/CLR : pure** et **CLR : safe** options sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Si votre code doit être sécurisé ou vérifiable, nous vous recommandons de porter à C#.

## <a name="mixed-clr"></a>Mixte (/ clr)

Assemblys mixtes (compilés avec **/CLR**), tous les deux non managée et parties managées, ce qui permet d’utiliser les fonctionnalités de .NET, tout en contenant du code natif. Ainsi, les applications et les composants à mettre à jour utiliser les fonctionnalités de .NET sans nécessiter que l’ensemble du projet être réécrites. À l’aide de Visual C++ permet de combiner du code managé et natif de cette manière est appelé l’interopérabilité C++. Pour plus d’informations, consultez [assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md) et [natif et l’interopérabilité .NET](../dotnet/native-and-dotnet-interoperability.md).

Appels effectués à partir d’assemblys managés dans des DLL natives via P/Invoke compilera, mais peuvent échouer lors de l’exécution en fonction des paramètres de sécurité.

Il existe un scénario de programmation qui passera le compilateur, mais cela entraîne un assembly non vérifiable : appeler une fonction virtuelle via une instance d’objet à l’aide de l’opérateur de résolution de portée.  Par exemple : `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Voir aussi

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
