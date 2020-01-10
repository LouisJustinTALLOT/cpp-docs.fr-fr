---
title: Plateformes prises en charge (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793828"
---
# <a name="supported-platforms-visual-c"></a>Plateformes prises en charge (Visual C++)

Les applications générées à l'aide de Visual Studio peuvent être ciblées pour différentes plateformes, comme suit.

|Système d'exploitation|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|x|x|||
|Windows Server 2008|x|x|||
|Windows 7|x|x|||
|Windows Server 2012 R2|x|x|||
|Windows 8|x|x|x||
|Windows 8.1|x|x|x||
|Windows 10|x|x|x|x|
|Android \*\*|x|x|x|x|
|iOS \*\*|x|x|x|x|
|Linux \*\*\*|x|x|x|x|

\* vous pouvez utiliser l’ensemble d’outils de plateforme Windows XP inclus dans Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 et Visual Studio 2012 Update 1 pour générer des projets Windows XP et Windows Server 2003. Pour plus d’informations sur la façon d’utiliser cet ensemble d’outils de plateforme, consultez [Configuration des programmes pour Windows XP](../build/configuring-programs-for-windows-xp.md). Pour plus d’informations sur la modification de l’ensemble d’outils de plateforme, consultez [Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* Vous pouvez installer la charge de travail **Développement mobile en C++** dans le programme d’installation pour Visual Studio 2017 et ultérieur. Lors de l’installation de Visual Studio 2015, choisissez le composant facultatif **Visual C++ pour le développement mobile multiplateforme** pour cibler les plateformes iOS ou Android. Pour obtenir des instructions, consultez [Installer Visual C++ pour le développement mobile multiplateforme](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Pour générer du code iOS, vous devez disposer d’un ordinateur Mac et satisfaire à d’autres exigences. Pour obtenir une liste des prérequis et des instructions détaillées, consultez [Installer et configurer les outils de génération pour iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Vous pouvez générer du code x86 ou ARM en fonction du matériel cible. Utilisez des configurations x86 pour générer pour le simulateur iOS, pour l'émulateur Microsoft Visual Studio pour Android et pour certains appareils Android. Utilisez des configurations ARM pour générer des applications pour les appareils iOS et la plupart des appareils Android.

\*\*\* Lors de l’installation de Visual Studio 2017 et ultérieur, vous pouvez installer la charge de travail **Développement Linux avec C++** pour cibler les plateformes Linux. Pour obtenir des instructions, consultez [Télécharger, installer et configurer la charge de travail Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Cet ensemble d’outils compile votre exécutable sur la machine cible, ce qui vous permet de générer du code pour toutes les architectures prises en charge.

\*\*\*\* La prise en charge ARM64 est disponible dans Visual Studio 2017 et ultérieur.

Pour plus d’informations sur la configuration d’une plateforme cible, consultez [Guide pratique pour configurer des projets Visual C++ afin de cibler des plateformes x64 64 bits](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Voir aussi

- [Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Bien démarrer](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
