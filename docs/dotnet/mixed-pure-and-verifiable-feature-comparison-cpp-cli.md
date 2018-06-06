---
title: Comparaison entre les fonctionnalités mixte, pure et vérifiable (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cb1b2ba71277415fd1ba5124f6120cc2f2c995d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704709"
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Comparaison entre les fonctionnalités mixte, pure et vérifiable (C + c++ / CLI)

Cette rubrique compare les fonctionnalités des différents **/CLR** modes de compilation. Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

> [!IMPORTANT]
> Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

## <a name="feature-comparison"></a>Comparaison des fonctionnalités

|Fonctionnalité|Mixte (/ clr)|Pure (/ clr : pure)|Sécurisé (/ CLR : safe)|Informations connexes|
|-------------|---------------------|-------------------------|-------------------------|-------------------------|
|Bibliothèque CRT|Prise en charge|deprecated||[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)|
|MFC/ATL|Prise en charge|||[Les Applications de bureau MFC](../mfc/mfc-desktop-applications.md) &#124; [vue d’ensemble de la classe](../atl/atl-class-overview.md)|
|Fonctions non managées|Prise en charge|||[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)|
|Données non managées|Prise en charge|deprecated||[Code pur et vérifiable (C++-CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|
|Peut être appelé à partir de fonctions non managées|Prise en charge||||
|Prend en charge l’appel de fonctions non managées|Prise en charge|deprecated|deprecated|[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|
|Prend en charge la réflexion|DLL uniquement|deprecated|deprecated|[Réflexion (C++-CLI)](../dotnet/reflection-cpp-cli.md)|

## <a name="see-also"></a>Voir aussi

- [Code pur et vérifiable (C++-CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)