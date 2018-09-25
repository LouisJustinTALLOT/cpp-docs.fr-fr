---
title: Redistribution des composants à l’aide de modules de fusion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f4dda75533b2c16405485f8bb2f3ab9982033ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425559"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribution des composants à l’aide de modules de fusion

Visual Studio inclut des [modules de fusion](/windows/desktop/Msi/about-merge-modules) pour chaque composant Visual C++ autorisé à être redistribué avec une application. Lorsqu’un module de fusion est compilé dans un fichier d’installation de Windows Installer, il permet le déploiement de certaines DLL sur des ordinateurs comportant une plateforme spécifique. Dans votre fichier d’installation, indiquez que les modules de fusion sont des composants requis pour votre application. Lors de l’installation de Visual Studio, les modules de fusion sont installés dans \Program Files\Common Files\Merge Modules\\. (Seules les versions non Debug des DLL Visual C++ peuvent être redistribuées.) Pour plus d’informations et un lien vers une liste des modules de fusion autorisés à la redistribution, consultez [Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md).

Vous pouvez utiliser des modules de fusion pour permettre l’installation des DLL redistribuables Visual C++ dans le dossier %SYSTEMROOT%\system32\. (Visual Studio lui-même utilise cette technique.) Toutefois, l’installation dans ce dossier échouera à moins que l’utilisateur chargé de l’installation possède des droits d’administrateur.

Nous vous déconseillons d’utiliser des modules de fusion à moins que vous n’ayez pas à assurer la maintenance de votre application et qu’il n’existe pas de dépendances sur plus d’une version des DLL. Les modules de fusion applicables à différentes versions de la même DLL ne peuvent être inclus dans un programme d’installation. De plus, les modules de fusion rendent difficile la maintenance des DLL indépendamment de l’application. À la place, nous vous recommandons d’installer un package redistribuable Visual C++.

## <a name="see-also"></a>Voir aussi

[Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md)