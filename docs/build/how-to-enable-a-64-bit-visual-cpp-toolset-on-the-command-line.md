---
title: 'Procédure : Activer un ensemble d’outils 64 bits MSVC sur la ligne de commande'
ms.date: 03/29/2018
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: 8436254a3d8c5c1dae018c2309ceaad7bd5b2408
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188910"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Procédure : Activer une version 64 bits, x64 hébergés ensemble d’outils MSVC sur la ligne de commande

Visual Studio inclut les compilateurs C++, les éditeurs de liens et les autres outils que vous pouvez utiliser pour créer des versions spécifiques à la plateforme de vos applications pouvant s’exécuter sur les systèmes d’exploitation Windows 32 bits, 64 bits ou basé sur ARM. Autres charges de travail Visual Studio facultatifs vous permettent d’utiliser des outils C++ pour cibler d’autres plateformes, telles qu’iOS, Android et Linux. L’architecture de build par défaut utilise des outils 32 bits, hébergé de x86 pour générer le code de Windows 32 bits, natif x86. Toutefois, vous avez probablement un ordinateur 64 bits. Vous pouvez tirer parti du processeur et de l’espace de mémoire disponible pour le code 64 bits à l’aide de l’ensemble d’outils 64 bits, hébergés en x64 64 lorsque vous générez du code pour x86, x64 ou les processeurs ARM.

> [!NOTE]
> Pour plus d’informations sur les outils spécifiques qui sont inclus dans chaque édition de Visual Studio, consultez [outils Visual C++ et des fonctionnalités dans les éditions de Visual Studio](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Pour plus d’informations sur l’utilisation de l’IDE Visual Studio pour créer des applications 64 bits, consultez [Comment : configurer des projets Visual C++ pour cibler des plateformes x64 64 bits](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Lorsque vous installez une charge de travail C++ dans le programme d’installation de Visual Studio, il installe toujours 32 bits, x86-hébergé, outils natifs et croisés du compilateur pour générer le code x86 et x64. Si vous incluez la charge de travail de plateforme Windows universelle, il installe également des outils hébergés x86 un compilateur croisé pour générer du code d’ARM. Si vous installez ces charges de travail sur un x64 64 64 bits, processeur, vous également obtenir 64 bits natif et les outils du compilateur pour générer des x86, x 64 et ARM de code. Les outils 32 bits et 64 bits génèrent un code identique, mais les outils 64 bits prennent en charge davantage de mémoire pour les symboles d’en-têtes précompilés et Whole Program Optimization ([/GL](reference/gl-whole-program-optimization.md) et [/LTCG](reference/ltcg-link-time-code-generation.md)) options. Si vous rencontrez des limites de mémoire lorsque vous utilisez les outils 32 bits, essayez les outils 64 bits.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Utilisez un raccourci d’invite de commandes développeur hébergés 64 bits

Lorsque Visual Studio est installé sur un système d’exploitation de Windows 64 bits, les raccourcis d’invite de commandes de développement supplémentaires pour 64 bits, hébergés en x64 64 natifs et croisés compilateurs sont disponibles. Pour accéder à ces invites de commandes sur Windows 10, dans le **Démarrer** menu, ouvrez le dossier correspondant à votre version de Visual Studio, par exemple **Visual Studio 2017**, puis choisissez une de le x64 natif ou cross-tool invites de commandes développeur. Pour accéder à ces invites de commandes sur Windows 8, dans le **Démarrer** écran, ouvrez **toutes les applications**. Sous l’en-tête pour la version installée de Visual Studio, ouvrez le **Visual Studio** dossier (dans les versions antérieures de Visual Studio, il peut être nommé **Visual Studio Tools**). Dans les versions antérieures de Windows, choisissez **Démarrer**, développez **tous les programmes**, le dossier correspondant à votre version de **Visual Studio** (et dans les versions antérieures de Visual Studio,  **Visual Studio Tools**). Pour plus d’informations, consultez [Raccourcis de l’invite de commandes développeur](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Utiliser Vcvarsall.bat une architecture de build hébergé 64 bits

N’importe quel natif ou les outils du compilateur configurations de build peuvent être utilisées sur la ligne de commande en exécutant la vcvarsall.bat fichier de commandes. Ce fichier de commande configure le chemin d’accès et des variables d’environnement qui permettent un particulier build architecture dans une fenêtre d’invite de commandes existante. Pour obtenir des instructions spécifiques, consultez [emplacements de fichiers de commandes développeur](building-on-the-command-line.md#developer_command_file_locations).

## <a name="see-also"></a>Voir aussi

[Configurer des projets C++ pour x64 64 64 bits, cibles](configuring-programs-for-64-bit-visual-cpp.md)<br/>
