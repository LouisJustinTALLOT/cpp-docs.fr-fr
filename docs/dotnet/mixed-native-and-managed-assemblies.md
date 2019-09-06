---
title: Assemblys mixtes (natif et managé)
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311931"
---
# <a name="mixed-native-and-managed-assemblies"></a>Assemblys mixtes (natifs et managés)

Les assemblys mixtes peuvent contenir à la fois des instructions machine non managées et des instructions MSIL. Cela leur permet d’appeler et d’être appelés par les composants .NET, tout en conservant C++ la compatibilité avec les bibliothèques natives. À l’aide d’assemblys mixtes, les développeurs peuvent créer des applications à C++ l’aide d’un mélange de .net et de code natif.

Par exemple, une bibliothèque existante composée entièrement de code C++ natif peut être transmise à la plate-forme .net en recompilant un seul module avec le commutateur de compilateur **/CLR** . Ce module est ensuite en mesure d’utiliser les fonctionnalités .NET, mais il reste compatible avec le reste de l’application. Il est même possible de choisir la compilation managée et native sur une base fonction par fonction dans le même fichier (voir [managé, non managé](../preprocessor/managed-unmanaged.md)).

Visual C++ prend uniquement en charge la génération d’assemblys managés mixtes à l’aide de l’option du compilateur **/CLR** . Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017. Si vous avez besoin d’assemblys managés purs ou vérifiables, nous vous recommandons de C#les créer à l’aide de.

Les versions antérieures de l' C++ ensemble d’outils du compilateur Microsoft prenait en charge la génération de trois types distincts d’assemblys managés : mixte, pur et vérifiable. Les deux derniers sont traités dans le [Code pur et vérifiable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>Dans cette section

[Guide pratique : Migrer vers/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Décrit les étapes recommandées pour l’introduction ou la mise à niveau de la fonctionnalité .NET dans votre application.

[Guide pratique pour Compiler du code MFC et ATL à l’aide de/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.

[Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Décrit le problème de « verrouillage du chargeur » et les solutions.

[Prise en charge de bibliothèque pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Explique comment utiliser des bibliothèques natives dans des compilations **/CLR** .

[Considérations sur les performances](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Décrit les implications en matière de performances des assemblys mixtes et du marshaling de données.

[Domaines d’application et Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Décrit la prise C++ en charge visuelle pour les domaines d’application.

[Double médiateur](../dotnet/double-thunking-cpp.md)<br/>
Décrit les implications en termes de performances d’un point d’entrée natif pour une fonction managée.

[Éviter des exceptions lors de l’arrêt du CLR lors de l’utilisation d’objets COM générés avec/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Explique comment garantir l’arrêt correct d’une application managée qui utilise un objet COM compilé avec **/CLR**.

[Guide pratique : créer une application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Explique comment créer une application du Common Language Runtime d’un niveau de confiance C++ partiel à l’aide de Visual en supprimant la dépendance sur msvcm90. dll.

Pour plus d’informations sur les instructions de codage pour les assemblys mixtes, consultez l’article MSDN [vue d’ensemble de l’interopérabilité du code managé/non géré](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Voir aussi

- [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
