---
title: Création de programmes C/C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2792b49d7d3d3f107e39931ff62e6c4137c9c5ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723266"
---
# <a name="building-cc-programs"></a>Génération de programmes C/C++

Vous pouvez générer des projets Visual C++ dans Visual Studio ou sur la ligne de commande. L’IDE Visual Studio utilise [MSBuild](../build/msbuild-visual-cpp.md) pour générer des projets et solutions. Sur la ligne de commande, vous pouvez utiliser le compilateur C/C++ (cl.exe) et l'éditeur de liens (link.exe) pour générer des projets simples. Pour générer des projets plus complexes sur la ligne de commande, vous pouvez utiliser MSBuild ou [NMAKE](../build/nmake-reference.md). Pour une vue d’ensemble sur l’utilisation de Visual Studio pour générer des projets et solutions, consultez [compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio).

## <a name="in-this-section"></a>Dans cette section

[Génération de projets C++ dans Visual Studio](../ide/building-cpp-projects-in-visual-studio.md) explique comment utiliser l’IDE Visual Studio pour générer votre projet C/C++.

[Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) explique comment utiliser le compilateur de ligne de commande C/C++ et outils de génération qui sont inclus dans Visual Studio.

[Création d’Applications isolées C/C++ et les assemblys côte à côte](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) décrit le modèle de déploiement pour les applications de bureau de Windows, basée sur l’idée d’applications isolées et assemblys côte à côte.

[Référence de génération C/C++](../build/reference/c-cpp-building-reference.md) fournit des liens vers des articles de référence sur la génération de programmes en C++, du compilateur et les options de l’éditeur de liens, et divers outils de génération.

[Configurer Visual C++ pour x64 64 64 bits, cibles](../build/configuring-programs-for-64-bit-visual-cpp.md) décrit comment configurer Visual Studio et la ligne de commande pour utiliser l’ensemble d’outils 64 bits et cibler des architectures 64 bits et aborde les problèmes courants de migration quand du code est transposé à 64 bits architectures.

[Configurer Visual C++ pour les processeurs ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md) décrit les conventions utilisées par les processeurs ARM et traite des problèmes courants de migration lorsque le code est transposé sur les architectures ARM.

[Configuration des programmes pour Windows XP](../build/configuring-programs-for-windows-xp.md) explique comment définir l’ensemble d’outils de plateforme pour le développement de Windows XP.

## <a name="related-sections"></a>Rubriques connexes

[Compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio) décrit le de génération Visual Studio système et les outils.