---
title: Créer un projet C++ MSBuild Linux dans Visual Studio
ms.date: 10/15/2020
description: Créez un nouveau projet Linux basé sur MSBuild dans Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: dddb9dbdee4cefc58a2bd5ccefa493b25e1c9f24
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176306"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>Créer un projet C++ MSBuild Linux dans Visual Studio

::: moniker range="vs-2015"

Les projets Linux sont disponibles dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2017"

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Pour la compilation multiplateforme, nous vous recommandons d’utiliser CMake. La prise en charge de CMake est plus complète dans Visual Studio 2019. Si CMake n’est pas une option et que vous disposez d’une solution Windows Visual Studio que vous souhaitez étendre pour la compilation pour Linux, vous pouvez ajouter un projet Visual Studio Linux à la solution Windows, ainsi qu’un projet **éléments partagés** . Placez le code qui est partagé entre les deux plateformes dans le projet éléments partagés et ajoutez une référence à ce projet à partir des projets Windows et Linux.

## <a name="to-create-a-new-linux-project"></a>Pour créer un projet Linux

Pour créer un projet Linux dans Visual Studio 2017, procédez comme suit :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Sélectionnez le nœud **Visual C++ > Multiplateforme > Linux**, puis le type de projet à créer. Entrez un **Nom** et un **Emplacement**, puis choisissez **OK**.

   ![Capture d’écran montrant la boîte de dialogue Nouveau projet avec Visual C plus > multiplateforme > Linux sélectionné, tous les types de projets appelés et les zones de texte nom et emplacement également appelées.](media/newproject.png)

   | Type de projet | Description |
   | ------------ | --- |
   | **Clignotement (Raspberry)** | Projet ciblé pour un appareil Raspberry Pi, avec un exemple de code qui fait clignoter une LED |
   | **Application console (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux, avec un exemple de code qui fait sortir un texte vers la console |
   | **Projet vide (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code |
   | **Projet Makefile (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux, généré à l’aide d’un système de génération Makefile standard |

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet MSBuild Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Quand vous créez un projet C++ pour Linux dans Visual Studio, vous pouvez choisir de créer un projet Visual Studio ou un projet CMake. Cet article décrit comment créer un projet Visual Studio. En général, pour les nouveaux projets qui peuvent inclure du code open source ou que vous envisagez de compiler pour le développement multiplateforme, nous vous recommandons d’utiliser CMake avec Visual Studio. Avec un projet CMake, vous pouvez générer et déboguer le même projet sur Windows et Linux. Pour plus d’informations, consultez [créer et configurer un projet cmake Linux](cmake-linux-project.md).

Si vous disposez d’une solution Windows Visual Studio que vous souhaitez étendre pour la compilation pour Linux, et que CMake n’est pas une option, vous pouvez ajouter un projet Visual Studio Linux à la solution Windows, ainsi qu’un projet d' **éléments partagés** . Placez le code qui est partagé entre les deux plateformes dans le projet éléments partagés et ajoutez une référence à ce projet à partir des projets Windows et Linux.

## <a name="create-a-new-linux-project"></a>Créer un projet Linux

Pour créer un projet Linux dans Visual Studio 2019, procédez comme suit :

1. Sélectionnez **fichier > nouveau projet** dans Visual Studio ou appuyez sur **Ctrl + Maj + N**. La boîte de dialogue créer un nouveau projet s’affiche.
1. Dans la zone de texte **Rechercher des modèles** , entrez **Linux** pour répertorier les modèles disponibles pour les projets Linux.
1. Sélectionnez le type de projet à créer, par exemple **application console**, puis cliquez sur **suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

   ![Capture d’écran de la boîte de dialogue Nouveau projet avec la liste déroulante langue définie sur C++ et la liste déroulante plateforme définie sur Linux.](media/newproject-vs2019.png)

   | Type de projet | Description |
   | ------------ | --- |
   | **Projet Raspberry pi** | Projet ciblé pour un appareil Raspberry Pi, avec un exemple de code qui fait clignoter une LED |
   | **Application console** | Projet ciblé pour n’importe quel ordinateur Linux, avec un exemple de code qui fait sortir un texte vers la console |
   | **Projet vide** | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code |
   | **Projet Makefile** | Projet ciblé pour n’importe quel ordinateur Linux, généré à l’aide d’un système de génération Makefile standard |
   | **Projet CMake** | Projet ciblé pour n’importe quel ordinateur Linux, créé à l’aide du système de génération CMake |

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet Linux MSBuild](configure-a-linux-project.md)

::: moniker-end
