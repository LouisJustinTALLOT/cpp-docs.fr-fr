---
title: Créer un projet Linux C++ dans Visual Studio
ms.date: 10/24/2019
description: Créez un nouveau projet Linux basé sur MSBuild dans Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 1e79dd50756b71aabae7ccec75e57178898e7720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364350"
---
# <a name="create-a-new-linux-project"></a>Créer un projet Linux

::: moniker range="vs-2015"

Les projets Linux sont disponibles dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2017"

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Pour la compilation multiplateforme, nous vous recommandons d’utiliser CMake. Le support CMake est plus complet dans Visual Studio 2019. Si CMake n’est pas une option, et que vous disposez d’une solution Windows Visual Studio existante que vous souhaitez étendre pour compiler pour Linux, vous pouvez ajouter un projet Visual Studio Linux à la solution Windows, ainsi qu’un projet **d’objets partagés.** Mettez le code qui est partagé entre les deux plates-formes dans le projet d’éléments partagés, et ajoutez une référence à ce projet à partir des projets Windows et Linux.

## <a name="to-create-a-new-linux-project"></a>Pour créer un projet Linux

Pour créer un nouveau projet Linux dans Visual Studio 2017, suivez ces étapes :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Sélectionnez le nœud **Visual C++ > Multiplateforme > Linux**, puis le type de projet à créer. Entrez un **Nom** et un **Emplacement**, puis choisissez **OK**.

   ![Nouveau projet Linux](media/newproject.png)

   | Type de projet | Description |
   | ------------ | --- |
   | **Clignotement (Raspberry)**           | Projet ciblé pour un appareil Raspberry Pi, avec un exemple de code qui fait clignoter une LED |
   | **Application console (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux, avec un exemple de code qui fait sortir un texte vers la console |
   | **Projet vide (Linux)**       | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code |
   | **Projet Makefile (Linux)**    | Projet ciblé pour n’importe quel ordinateur Linux, généré à l’aide d’un système de génération Makefile standard |

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, voir [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Quand vous créez un projet C++ pour Linux dans Visual Studio, vous pouvez choisir de créer un projet Visual Studio ou un projet CMake. Cet article décrit comment créer un projet Visual Studio. En général, pour les nouveaux projets qui pourraient inclure du code open source ou que vous avez l’intention de compiler pour le développement multiplateforme, nous vous recommandons d’utiliser CMake avec Visual Studio. Avec un projet CMake, vous pouvez construire et déboçonner le même projet sur Windows et Linux. Pour plus d’informations, voir [Créer et configurer un projet Linux CMake](cmake-linux-project.md).

Si vous avez une solution Existante De Windows Visual Studio que vous souhaitez étendre à compiler pour Linux, et CMake n’est pas une option, alors vous pouvez ajouter un projet Visual Studio Linux à la solution Windows, avec un projet **d’éléments partagés.** Mettez le code qui est partagé entre les deux plates-formes dans le projet d’éléments partagés, et ajoutez une référence à ce projet à partir des projets Windows et Linux.

## <a name="to-create-a-new-linux-project"></a>Pour créer un projet Linux

Pour créer un nouveau projet Linux dans Visual Studio 2019, suivez ces étapes :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Définissez le **Langage** sur **C++** et recherchez « Linux ». Sélectionnez le type de projet à créer, puis choisissez **Suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

   ![Nouveau projet Linux](media/newproject-vs2019.png)

   | Type de projet | Description |
   | ------------ | --- |
   | **Clignotement (Raspberry)**           | Projet ciblé pour un appareil Raspberry Pi, avec un exemple de code qui fait clignoter une LED |
   | **Application console (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux, avec un exemple de code qui fait sortir un texte vers la console |
   | **Projet vide (Linux)**       | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code |
   | **Projet Makefile (Linux)**    | Projet ciblé pour n’importe quel ordinateur Linux, généré à l’aide d’un système de génération Makefile standard |

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet Linux](configure-a-linux-project.md)

::: moniker-end
