---
description: 'En savoir plus sur : assemblys mixtes (natifs et managés)'
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
ms.openlocfilehash: b96ccb5a521cf009f7feabef01a292ac805b0b4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253635"
---
# <a name="mixed-native-and-managed-assemblies"></a>Assemblys mixtes (natifs et managés)

Les assemblys mixtes peuvent contenir à la fois des instructions machine non managées et des instructions MSIL. Cela leur permet d’appeler et d’être appelés par les composants .NET, tout en conservant la compatibilité avec les bibliothèques C++ natives. À l’aide d’assemblys mixtes, les développeurs peuvent créer des applications à l’aide d’un mélange de code .NET et C++ natif.

Par exemple, une bibliothèque existante composée entièrement de code C++ natif peut être transmise à la plate-forme .NET en recompilant un seul module avec le commutateur de compilateur **/CLR** . Ce module est ensuite en mesure d’utiliser les fonctionnalités .NET, mais il reste compatible avec le reste de l’application. Il est même possible de choisir la compilation managée et native sur une base fonction par fonction dans le même fichier (voir [managé, non managé](../preprocessor/managed-unmanaged.md)).

Visual C++ prend en charge uniquement la génération d’assemblys managés mixtes à l’aide de l’option du compilateur **/CLR** . Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017. Si vous avez besoin d’assemblys managés purs ou vérifiables, nous vous recommandons de les créer à l’aide de C#.

Les versions antérieures de l’ensemble d’outils du compilateur Microsoft C++ prenait en charge la génération de trois types distincts d’assemblys managés : mixte, pur et vérifiable. Les deux derniers sont traités dans du [Code pur et vérifiable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>Dans cette section

[Comment : effectuer une migration vers/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Décrit les étapes recommandées pour l’introduction ou la mise à niveau de la fonctionnalité .NET dans votre application.

[Comment : compiler du code MFC et ATL à l’aide de/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.

[Initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Décrit le problème de « verrouillage du chargeur » et les solutions.

[Prise en charge des bibliothèques pour les assemblys mixtes](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Explique comment utiliser des bibliothèques natives dans des compilations **/CLR** .

[Considérations relatives aux performances](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Décrit les implications en matière de performances des assemblys mixtes et du marshaling de données.

[Domaines d’application et Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Traite de la prise en charge de Visual C++ pour les domaines d’application.

[Double conversion de code (thunking)](../dotnet/double-thunking-cpp.md)<br/>
Décrit les implications en termes de performances d’un point d’entrée natif pour une fonction managée.

[Éviter des exceptions lors de l’arrêt du CLR lors de l’utilisation d’objets COM générés avec/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Explique comment garantir l’arrêt correct d’une application managée qui utilise un objet COM compilé avec **/CLR**.

[Comment : créer une application partiellement approuvée en supprimant la dépendance sur la DLL de bibliothèque CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Explique comment créer une application du Common Language Runtime d’un niveau de confiance partiel à l’aide de Visual C++ en supprimant la dépendance sur msvcm90.dll.

Pour plus d’informations sur les instructions de codage pour les assemblys mixtes, consultez [une vue d’ensemble de l’interopérabilité du code managé/non managé](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Voir aussi

- [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
