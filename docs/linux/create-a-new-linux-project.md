---
title: Créer un projet Linux C++ dans Visual Studio
ms.date: 06/07/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: e39e60c906901420a4809c22b4f4e71d3b621da1
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821636"
---
# <a name="create-a-new-linux-project"></a>Créer un projet Linux

::: moniker range="vs-2015"

Les projets Linux sont disponibles dans Visual Studio 2017 et ultérieur.

::: moniker-end

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Quand vous créez un projet C++ pour Linux dans Visual Studio, vous pouvez choisir de créer un projet Visual Studio ou un projet CMake. Cet article décrit comment créer un projet Visual Studio. Pour plus d’informations sur la façon de créer des projets CMake et d’utiliser des projets existants, consultez [Configurer un projet CMake Linux](cmake-linux-project.md).

## <a name="to-create-a-new-linux-project"></a>Pour créer un projet Linux

Pour créer un projet Linux dans Visual Studio, effectuez les étapes suivantes :

::: moniker range="vs-2019"

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Définissez le **Langage** sur **C++** et recherchez « Linux ». Sélectionnez le type de projet à créer, puis choisissez **Suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

   ![Nouveau projet Linux](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Sélectionnez le nœud **Visual C++ > Multiplateforme > Linux**, puis le type de projet à créer. Entrez un **Nom** et un **Emplacement**, puis choisissez **OK**.

   ![Nouveau projet Linux](media/newproject.png)

::: moniker-end

   | Type de projet | Description |
   | ------------ | --- |
   | **Clignotement (Raspberry)**           | Projet ciblé pour un appareil Raspberry Pi, avec un exemple de code qui fait clignoter une LED |
   | **Application console (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux, avec un exemple de code qui fait sortir un texte vers la console |
   | **Projet vide (Linux)**       | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code |
   | **Projet Makefile (Linux)**    | Projet ciblé pour n’importe quel ordinateur Linux, généré à l’aide d’un système de génération Makefile standard |

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet Linux](configure-a-linux-project.md)
