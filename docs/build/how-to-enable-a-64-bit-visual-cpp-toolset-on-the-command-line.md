---
title: 'Comment : activer un ensemble d’outils MSVC bits 64 sur la ligne de commande'
ms.date: 07/24/2019
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
ms.openlocfilehash: 60399994cd5fc2f39efeadc6ffcf917138aada37
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078541"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Comment : activer un ensemble d’outils MSVC hébergé x64 64 bits sur la ligne de commande

Visual Studio inclut des compilateurs C++, des éditeurs de liens et d’autres outils que vous pouvez utiliser pour créer des versions spécifiques de la plateforme de vos applications pouvant s’exécuter sur les systèmes d’exploitation Windows 32 bits, 64 bits ou ARM. D’autres charges de travail Visual Studio facultatives vous permettent d’utiliser des outils C++ pour cibler d’autres plateformes, telles qu’iOS, Android et Linux. L’architecture de build par défaut utilise des outils x86 32 bits pour générer le code Windows x86 natif 32 bits. Toutefois, vous avez probablement un ordinateur 64 bits. Quand Visual Studio est installé sur un système d’exploitation Windows 64 bits, des raccourcis supplémentaires d’invite de commandes développeur pour les compilateurs natifs et croisés x64 64 bits sont disponibles. Vous pouvez tirer parti du processeur et de l’espace mémoire disponible pour le code 64 bits en utilisant l’ensemble d’outils x64 64 bits quand vous générez du code pour des processeurs x86, x64 ou ARM.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Utilisez un raccourci d’invite de commandes développeur 64 bits

Pour accéder à ces invites de commandes sur Windows 10, dans le menu **Démarrer**, ouvrez le dossier correspondant à votre version de Visual Studio, par exemple **Visual Studio 2019**, puis choisissez une des invites de commandes développeur d’un outil croisé ou natif x64.

![Invite de commandes des outils natifs x64](media/x64-native-tools-command-prompt.png "Outils natifs x64 du menu Démarrer")

Pour accéder à ces invites de commandes sur Windows 8, sur l’écran **Démarrer**, ouvrez **Toutes les applications**. Sous l’intitulé correspondant à la version installée de Visual Studio, ouvrez le dossier **Visual Studio** (dans les versions antérieures de Visual Studio, il peut être nommé **Visual Studio Tools**). Dans les versions antérieures de Windows, choisissez **Démarrer**, développez **Tous les programmes**, puis le dossier correspondant à votre version de **Visual Studio** (et sur les versions antérieures de Visual Studio,  **Visual Studio Tools**). Pour plus d’informations, consultez [Raccourcis de l’invite de commandes développeur](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Utiliser Vcvarsall.bat pour définir une architecture de build 64 bits

Vous pouvez utiliser n’importe quelle configuration de build des outils de compilation croisés ou natifs sur la ligne de commande en exécutant le fichier de commandes vcvarsall.bat. Ce fichier de commande configure le chemin et les variables d’environnement qui créent une architecture de build particulière dans une fenêtre d’invite de commandes existante. Pour des instructions spécifiques, consultez [Emplacements des fichiers de commandes développeur](building-on-the-command-line.md#developer_command_file_locations).

## <a name="remarks"></a>Notes

> [!NOTE]
> Pour plus d’informations sur les outils spécifiques qui sont inclus dans chaque édition de Visual Studio, consultez [Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Pour plus d’informations sur l’utilisation de l’IDE de Visual Studio pour créer des applications 64 bits, consultez Guide pratique [pour configurer des projets C++ visuels pour cibler des plates-formes x64 64 bits](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Quand vous installez une charge de travail C++ dans Visual Studio Installer, celui-ci installe toujours des outils de compilation croisés et natifs x86 32 bits pour la génération de code x86 et x64. Si vous incluez la charge de travail UWP, il installe également des outils de compilation croisés x86 pour la génération de code ARM. Si vous installez ces charges de travail sur un processeur x64 64 bits, vous obtenez également des outils de compilation natifs et croisés 64 bits pour la génération de code x86, x64 et ARM. Les outils 32 bits et 64 bits génèrent un code identique, mais les outils 64 bits prennent en charge davantage de mémoire pour les symboles d’en-têtes précompilés et les options d’optimisation de l’ensemble du programme ([/GL](reference/gl-whole-program-optimization.md) et [/LTCG](reference/ltcg-link-time-code-generation.md)). Si vous rencontrez des problèmes de mémoire lors de l’utilisation des outils 32 bits, essayez les outils 64 bits.

## <a name="see-also"></a>Voir aussi

[Configurer des projets C++ pour des cibles x64 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
