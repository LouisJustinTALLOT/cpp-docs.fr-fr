---
description: En savoir plus sur les plateformes prises en charge (Visual C++)
title: Plateformes prises en charge (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 80f8693a8cef7368953779d82100ce02e41f5cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207512"
---
# <a name="supported-platforms-visual-c"></a>Plateformes prises en charge (Visual C++)

Les applications générées à l'aide de Visual Studio peuvent être ciblées pour différentes plateformes, comme suit.

|Système d’exploitation|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|X|X|||
|Windows Server 2008|X|X|||
|Windows 7|X|X|||
|Windows Server 2012 R2|X|X|||
|Windows 8|X|X|X||
|Windows 8.1|X|X|X||
|Windows 10|X|X|X|X|
|Android \*\*|X|X|X|X|
|iOS \*\*|X|X|X|X|
|Linux \*\*\*|X|X|X|X|

\* Vous pouvez utiliser l’ensemble d’outils de plateforme Windows XP inclus dans Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 et Visual Studio 2012 Update 1 pour générer des projets Windows XP et Windows Server 2003. Pour plus d’informations sur la façon d’utiliser cet ensemble d’outils de plateforme, consultez [Configuration des programmes pour Windows XP](../build/configuring-programs-for-windows-xp.md). Pour plus d’informations sur la modification de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* Vous pouvez installer la charge de travail **Développement mobile en C++** dans le programme d’installation pour Visual Studio 2017 et ultérieur. Lors de l’installation de Visual Studio 2015, choisissez le composant facultatif **Visual C++ pour le développement mobile multiplateforme** pour cibler les plateformes iOS ou Android. Pour obtenir des instructions, consultez [Installer Visual C++ pour le développement mobile multiplateforme](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Pour générer du code iOS, vous devez disposer d’un ordinateur Mac et satisfaire à d’autres exigences. Pour obtenir une liste des prérequis et des instructions détaillées, consultez [Installer et configurer les outils de génération pour iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Vous pouvez générer du code x86 ou ARM en fonction du matériel cible. Utilisez des configurations x86 pour générer pour le simulateur iOS, pour l'émulateur Microsoft Visual Studio pour Android et pour certains appareils Android. Utilisez des configurations ARM pour générer des applications pour les appareils iOS et la plupart des appareils Android.

\*\*\* Lors de l’installation de Visual Studio 2017 et ultérieur, vous pouvez installer la charge de travail **Développement Linux avec C++** pour cibler les plateformes Linux. Pour obtenir des instructions, consultez [Télécharger, installer et configurer la charge de travail Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Cet ensemble d’outils compile votre exécutable sur la machine cible, ce qui vous permet de générer du code pour toutes les architectures prises en charge.

\*\*\*\* La prise en charge ARM64 est disponible dans Visual Studio 2017 et ultérieur.

Pour plus d’informations sur la configuration d’une plateforme cible, consultez [Guide pratique pour configurer des projets Visual C++ afin de cibler des plateformes x64 64 bits](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Voir aussi

- [Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Prise en main](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
