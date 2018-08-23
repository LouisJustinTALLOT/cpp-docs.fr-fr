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
ms.openlocfilehash: 2fa07308d04d14395b0ca9773e2a0c81ed0c2bc2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573344"
---
# <a name="building-cc-programs"></a>Génération de programmes C/C++

Vous pouvez générer des projets Visual C++ dans Visual Studio ou sur la ligne de commande. L’IDE Visual Studio utilise [MSBuild](../build/msbuild-visual-cpp.md) pour générer des projets et solutions. Sur la ligne de commande, vous pouvez utiliser le compilateur C/C++ (cl.exe) et l'éditeur de liens (link.exe) pour générer des projets simples. Pour générer des projets plus complexes sur la ligne de commande, vous pouvez utiliser MSBuild ou [NMAKE](../build/nmake-reference.md). Pour une vue d’ensemble sur l’utilisation de Visual Studio pour générer des projets et solutions, consultez [compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>Dans cette section  

[Génération de projets C++ dans Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
Explique comment utiliser l'IDE de Visual Studio pour générer un projet en C/C++.  
  
[Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md)  
Explique comment utiliser le compilateur en ligne de commande et les outils de génération C/C++ intégrés à Visual Studio.  
  
[Génération d’applications isolées et d’assemblys côte à côte C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
Décrit le modèle de déploiement pour des applications de bureau Windows en partant du principe qu'il s'agit d'applications isolées et d'assemblys côte à côte.  
  
[Référence de la génération C/C++](../build/reference/c-cpp-building-reference.md)  
Fournit des liens vers des articles de référence sur la génération de programmes en C++, les options de compilateur et d'éditeur de liens, ainsi que divers outils de génération.  
  
[Configurer Visual C++ pour des cibles x64 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Explique comment configurer Visual Studio et la ligne de commande pour utiliser l'ensemble d'outils 64 bits et cibler des architectures 64 bits, et traite des problèmes de migration souvent rencontrés quand du code est transposé sur des architectures 64 bits.  
  
[Configurer Visual C++ pour les processeurs ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
Décrit les conventions utilisées par les processeurs ARM et traite des problèmes de migration souvent rencontrés lors du transfert de code sur des architectures ARM.  
  
[Configuration des programmes pour Windows XP](../build/configuring-programs-for-windows-xp.md)  
Explique comment définir l’ensemble d’outils de plateforme pour cibler un développement Windows XP.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Décrit les outils et le système de génération Visual Studio.