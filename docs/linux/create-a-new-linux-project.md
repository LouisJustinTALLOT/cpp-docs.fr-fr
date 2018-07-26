---
title: Créer un projet Linux C++ dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: f64f8eaf09e92df3dd776180db5904af039d6ad7
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207968"
---
# <a name="create-a-new-linux-project"></a>Créer un projet Linux
Quand vous développez en C++ dans Visual Studio pour Linux, vous avez le choix de créer un projet Visual Studio ou un projet CMake. Cette rubrique décrit comment créer un projet Visual Studio. Pour plus d’informations sur les projets CMake, consultez [Configurer un projet CMake Linux](cmake-linux-project.md).

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

