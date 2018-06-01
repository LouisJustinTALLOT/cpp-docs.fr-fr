---
title: Code pur et vérifiable (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 453bb40e94c1d345adbe22f8792b59d1e584499a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704826"
---
# <a name="pure-and-verifiable-code-ccli"></a>Code pur et vérifiable (C + c++ / CLI)

Pour la programmation .NET, Visual C++ dans Visual Studio 2017 prend en charge la création d’assemblys mixtes à l’aide de la [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le **/CLR : pure** et **CLR : safe** options sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Si votre code doit être sécurisé ou vérifiable, puis nous vous recommandons de porter vers c#.

## <a name="mixed-clr"></a>Mixte (/ clr)

Assemblys mixtes (compilés avec **/CLR**), contiennent à la fois non managé et managés parties, ce qui permet d’utiliser les fonctionnalités de .NET, mais encore contiennent du code natif. Ainsi, les applications et des composants à mettre à jour utiliser les fonctionnalités .NET sans avoir à réécrire de l’ensemble du projet. À l’aide de Visual C++ permet de combiner le code managé et natif de cette manière est appelé l’interopérabilité C++. Pour plus d’informations, consultez [mixte (natif et managé) assemblys](../dotnet/mixed-native-and-managed-assemblies.md) et [natif et l’interopérabilité .NET](../dotnet/native-and-dotnet-interoperability.md).

Les appels effectués à partir d’assemblys managés dans des DLL natives via P/Invoke sont compilés mais risque d’échouer lors de l’exécution en fonction des paramètres de sécurité.

Il existe un scénario de programmation qui passera le compilateur mais le résultat sera dans un assembly non vérifiable : appel de fonction virtuelle via une instance d’objet à l’aide de l’opérateur de résolution de portée.  Par exemple : `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Voir aussi

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

