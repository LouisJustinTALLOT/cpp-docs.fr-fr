---
description: 'En savoir plus sur : redistribution des composants à l’aide de modules de fusion'
title: Redistribution des composants à l’aide de modules de fusion
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: ecfc2904be7451c96226e91ed8e7f98d565d35ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179900"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redistribution des composants à l’aide de modules de fusion

Visual Studio inclut des [modules de fusion](/windows/win32/Msi/about-merge-modules) pour chaque composant Visual C++ autorisé à être redistribué avec une application. Lorsqu’un module de fusion est compilé dans un fichier d’installation de Windows Installer, il permet le déploiement de certaines DLL sur des ordinateurs comportant une plateforme spécifique. Dans votre fichier d’installation, indiquez que les modules de fusion sont des composants requis pour votre application. Lors de l’installation de Visual Studio, les modules de fusion sont installés dans \Program Files\Common Files\Merge Modules\\. (Seules les versions sans débogage des dll de Visual C++ peuvent être redistribuées.) Pour plus d’informations et pour obtenir un lien vers une liste de modules de fusion concédés sous licence pour la redistribution, consultez redistribution des [fichiers de Visual C++](redistributing-visual-cpp-files.md).

Vous pouvez utiliser des modules de fusion pour permettre l’installation des DLL redistribuables Visual C++ dans le dossier %SYSTEMROOT%\system32\. (Visual Studio lui-même utilise cette technique.) Toutefois, l’installation dans ce dossier échouera à moins que l’utilisateur qui installe dispose de droits d’administrateur.

Nous vous déconseillons d'utiliser des modules de fusion à moins que vous n'ayez pas à assurer la maintenance de votre application et qu'il n'existe pas de dépendances sur plus d'une version des DLL. Les modules de fusion applicables à différentes versions de la même DLL ne peuvent être inclus dans un programme d'installation. De plus, les modules de fusion rendent difficile la maintenance des DLL indépendamment de l'application. À la place, nous vous recommandons d’installer un package redistribuable Visual C++.

## <a name="see-also"></a>Voir aussi

[Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md)
