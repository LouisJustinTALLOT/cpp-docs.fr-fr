---
title: Créer un projet Linux C++ dans Visual Studio
ms.date: 09/12/2018
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: bd5ab1d2bc1077f366082bf8767f8f690173ac8b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745158"
---
# <a name="create-a-new-linux-project"></a>Créer un projet Linux

Tout d’abord, vérifiez que la **charge de travail de développement Linux** pour Visual Studio est installée. Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Quand vous créez un projet C++ dans Visual Studio pour Linux, vous avez le choix entre créer un projet Visual Studio et créer un projet CMake. Cette rubrique décrit comment créer un projet Visual Studio. Pour plus d’informations sur la création de projets CMake et l’utilisation de projets existants, consultez [Configurer un projet CMake Linux](cmake-linux-project.md).

Pour créer un projet Linux dans Visual Studio, effectuez les étapes suivantes :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Sélectionnez le nœud **Visual C++ > Multiplateforme > Linux** et le type de projet que vous voulez créer, entrez un nom/emplacement, puis cliquez sur OK.

   ![Nouveau projet Linux](media/newproject.png)

   | Type de projet | Description
   | ------------ | ---
   | **Clignotement (Raspberry)**           | Projet ciblé pour un appareil Raspberry Pi avec un exemple de code écrit pour faire clignoter une LED
   | **Application console (Linux)** | Projet ciblé pour n’importe quel ordinateur Linux avec un exemple de code écrit afin de sortir un texte vers la console
   | **Projet vide (Linux)**       | Projet ciblé pour n’importe quel ordinateur Linux sans exemple de code écrit
   | **Projet Makefile (Linux)**    | Projet ciblé pour n’importe quel ordinateur Linux qui sera généré à l’aide d’un système de génération Makefile standard
