---
title: Redistribution des fichiers Visual C++
description: Visual Studio comprend des bibliothèques et des composants redistribuables que vous pouvez déployer avec votre application.
ms.date: 07/16/2020
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: a660e67b2664417438ea9fa7acddbde4c20c307a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924142"
---
# <a name="redistributing-visual-c-files"></a>Redistribution des fichiers Visual C++

> [!NOTE]
> Êtes-vous ici parce que vous recherchez un téléchargement de l’un des fichiers d’exécution de Visual C++ ? Accédez au [site Web Microsoft](https://www.microsoft.com/) et entrez **Visual C++ redistribuable** dans la zone de recherche. Téléchargez et installez le package redistribuable correspondant à l’architecture de votre ordinateur (par exemple, x64 si vous exécutez Windows 64 bits) et à la version de Visual C++ dont vous avez besoin (par exemple, 2015).

## <a name="redistributable-files-and-licensing"></a>Fichiers redistribuables et licences

Lorsque vous déployez une application, vous devez également déployer les fichiers qui sont requis pour sa prise en charge. Si l’un de ces fichiers est fourni par Microsoft, vérifiez si vous êtes autorisé à les redistribuer. Vous trouverez un lien vers les termes du contrat de licence Visual Studio dans l’IDE. Utilisez le lien termes du contrat de licence de la boîte de dialogue à propos de Microsoft Visual Studio. Ou, téléchargez les CLUF et licences appropriés à partir du répertoire de [licence](https://visualstudio.microsoft.com/license-terms/)de Visual Studio.

::: moniker range="msvc-160"

Pour afficher la « liste Redist » référencée dans la section « Code distribuable » des termes du contrat de licence logiciel Microsoft Visual Studio 2019, consultez [fichiers de code distribuable pour Microsoft Visual Studio 2019](/visualstudio/releases/2019/redistribution#-distributable-code-files-for-visual-studio-2019)

::: moniker-end

::: moniker range="msvc-150"

Pour afficher la « liste Redist » référencée dans la section « Code distribuable » des termes du contrat de licence logiciel Microsoft Visual Studio 2017, consultez [fichiers de code distribuable pour Microsoft Visual Studio 2017](/visualstudio/productinfo/2017-redistribution-vs#-distributable-code-files-for-visual-studio-2017).

::: moniker-end

::: moniker range="msvc-140"

Pour afficher la « liste Redist » référencée dans la section « Code distribuable » des termes du contrat de licence logiciel Microsoft Visual Studio 2015, consultez [fichiers de code distribuable pour Microsoft Visual Studio 2015](/visualstudio/productinfo/2015-redistribution-vs#-distributable-code-files-for-visual-studio-2015).

::: moniker-end

Pour plus d’informations sur les fichiers redistribuables, consultez [la page détermination des dll à redistribuer](determining-which-dlls-to-redistribute.md) et des [exemples de déploiement](deployment-examples.md).

## <a name="locate-the-redistributable-files"></a>Localiser les fichiers redistribuables

Pour déployer des fichiers redistribuables, vous pouvez utiliser les packages redistribuables installés par Visual Studio. Dans les versions de Visual Studio depuis 2017, ces fichiers sont nommés *`vc_redist.arm64.exe`* , *`vc_redist.x64.exe`* et *`vc_redist.x86.exe`* . Dans Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019, ils sont également disponibles sous les noms *`vcredist_x86.exe`* , *`vcredist_x64.exe`* et *`vcredist_arm.exe`* (2015 uniquement).

Le moyen le plus simple de rechercher les fichiers redistribuables consiste à utiliser des variables d’environnement définies dans une invite de commandes développeur. Dans la dernière version de Visual Studio 2019, vous trouverez les fichiers redistribuables dans le *`%VCINSTALLDIR%Redist\MSVC\v142`* dossier. Dans Visual Studio 2017 et Visual Studio 2019, ils sont également disponibles dans *`%VCToolsRedistDir%`* . Dans Visual Studio 2015, ces fichiers se trouvent dans *`%VCINSTALLDIR%redist\<locale>`* , où *`<locale>`* correspond aux paramètres régionaux des packages redistribuables.

Une autre option de déploiement consiste à utiliser des modules de fusion redistribuables ( *`.msm`* fichiers). Dans Visual Studio 2019, ces fichiers font partie d’un composant d’installation facultatif nommé **C++ 2019 Redistributable MSMs** dans le Visual Studio installer. Les modules de fusion sont installés par défaut dans le cadre d’une installation de C++ dans Visual Studio 2017 et Visual Studio 2015. Lorsqu’il est installé dans la dernière version de Visual Studio 2019, les modules de fusion redistribuables sont disponibles dans *`%VCINSTALLDIR%Redist\MSVC\v142\MergeModules`* . Dans Visual Studio 2019 et Visual Studio 2017, ils sont également disponibles dans *`%VCToolsRedistDir%MergeModules`* . Dans Visual Studio 2015, ils se trouvent dans *`Program Files [(x86)]\Common Files\Merge Modules`* .

## <a name="install-the-redistributable-packages"></a>Installer les packages redistribuables

Les packages redistribuables Visual C++ installent et inscrivent toutes les bibliothèques Visual C++. Si vous en utilisez un, exécutez-le en tant que composant requis sur le système cible avant d’installer votre application. Nous vous recommandons d'utiliser ces packages pour les déploiements car ils permettent une mise à jour automatique des bibliothèques Visual C++. Pour obtenir un exemple d’utilisation de ces packages, consultez [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide du package redistribuable Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Chaque package redistribuable Visual C++ vérifie l'existence d'une version plus récente sur l'ordinateur. Si une version plus récente est trouvée, le package n’est pas installé. Depuis Visual Studio 2015, les packages redistribuables affichent un message d'erreur indiquant que l'installation a échoué. Si un package est exécuté à l’aide de l' **`/quiet`** indicateur, aucun message d’erreur n’est affiché. Dans les deux cas, une erreur est enregistrée par le programme d'installation de Microsoft, et un résultat d'erreur est retourné à l'appelant. À partir des packages de Visual Studio 2015, vous pouvez éviter cette erreur en recherchant dans le Registre si une version plus récente est installée. Le numéro de la version installée actuelle est stocké dans la `HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\14.0\VC\Runtimes\{x86|x64|ARM}` clé. Le numéro de version est 14,0 pour Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019, car le dernier redistribuable est compatible binaire avec la version d' 2015. La clé est `ARM` , `x86` , ou `x64` selon les versions d’vcredist installées pour la plateforme. (Vous devez vérifier sous la sous `Wow6432Node` -clé uniquement si vous utilisez regedit pour afficher la version du package x86 installé sur une plateforme x64.) Le numéro de version est stocké dans la valeur de chaîne REG_SZ **`Version`** et également dans le jeu de valeurs,, **`Major`** **`Minor`** **`Bld`** et **`Rbld`** `REG_DWORD` . Pour éviter une erreur au moment de l’installation, vous devez ignorer l’installation du package redistribuable si la version actuellement installée est plus récente.

## <a name="install-the-redistributable-merge-modules"></a>Installer les modules de fusion redistribuables

Les modules de fusion redistribuables doivent être inclus dans le package Windows Installer (ou un package d’installation similaire) que vous utilisez pour déployer votre application. Pour plus d’informations, consultez [Redistribution à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md). Pour obtenir un exemple [, consultez Procédure pas à pas : déploiement d’une Application Visual C++ à l’aide d’un projet d’installation](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

## <a name="install-individual-redistributable-files"></a>Installer des fichiers redistribuables individuels

Il est également possible d’installer directement les dll redistribuables dans le *dossier local* de l’application. Il s’agit du dossier qui contient votre fichier d’application exécutable. Pour des raisons de maintenance, nous vous déconseillons d’utiliser cet emplacement d’installation.

## <a name="potential-run-time-errors"></a>Erreurs d’exécution potentielles

Si Windows ne peut pas trouver l’une des dll de la bibliothèque redistribuable requises par votre application, il peut afficher un message semblable à celui-ci : «cette application n’a pas pu démarrer, car la *bibliothèque* . dll est introuvable. La réinstallation de l’application peut résoudre ce problème.»

Pour résoudre ce genre d’erreur, assurez-vous que votre programme d’installation de l’application se génère correctement. Vérifiez que les bibliothèques redistribuables sont correctement déployées sur le système cible. Pour plus d’informations, consultez [Fonctionnement des dépendances d’une application Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-articles"></a>Articles connexes

[Redistribution à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md)\
Décrit comment utiliser Visual C++ modules de fusion redistribuables pour installer les bibliothèques Visual C++ Runtime en tant que DLL partagées dans le *`%windir%\system32\`* dossier.

[Redistribution de Visual C++ contrôles ActiveX](redistributing-visual-cpp-activex-controls.md)\
Décrit comment redistribuer une application qui utilise les contrôles ActiveX.

[Redistribution de la bibliothèque MFC](redistributing-the-mfc-library.md)\
Décrit comment redistribuer une application qui utilise MFC.

[Redistribution d’une application ATL](redistributing-an-atl-application.md)\
Décrit comment redistribuer une application qui utilise ATL. Depuis Visual Studio 2012, aucune bibliothèque redistribuable pour ATL n'est requise.

[Exemples de déploiement](deployment-examples.md)\
Fournit des liens vers des exemples qui illustrent le déploiement d'applications Visual C++.

[Déploiement d’applications de bureau](deploying-native-desktop-applications-visual-cpp.md)\
Présente les concepts et les technologies de déploiement de Visual C++.
