---
title: Redistribution des fichiers Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 46192fe7ff5b29c22a5001cc460c74f5ddf6d1bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167925"
---
# <a name="redistributing-visual-c-files"></a>Redistribution des fichiers Visual C++

> [!NOTE]
> Vous voulez télécharger un des fichiers Runtime Visual C++ ? Accédez au [site Web Microsoft](https://www.microsoft.com/) et entrez **Visual C++ Redistributable** dans la zone de recherche. Téléchargez et installez le package redistribuable correspondant à l’architecture de votre ordinateur (par exemple, x64 si vous exécutez Windows 64 bits) et à la version de Visual C++ dont vous avez besoin (par exemple, 2015).

Lorsque vous déployez une application, vous devez également déployer les fichiers qui sont requis pour sa prise en charge. Si l'un de ces fichiers est fourni par Microsoft, vérifiez si vous êtes autorisé à le redistribuer. Pour passer en revue les termes du contrat de licence de Visual Studio, consultez le lien des termes du contrat de licence dans la boîte de dialogue À propos de Microsoft Visual Studio dans l’IDE, ou téléchargez le fichier [Termes du contrat de licence logiciel Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/). Pour voir la « liste REDIST » référencée dans la section « Code distribuable » des Termes du contrat de licence logiciel Microsoft pour certaines éditions de Visual Studio, consultez [Code redistribuable pour Microsoft Visual Studio 2017 et pour le SDK Microsoft Visual Studio 2017 (inclut les utilitaires et les fichiers BuildServer)](/visualstudio/productinfo/2017-redistribution-vs) ou, pour Visual Studio 2015, consultez [Code distribuable pour Microsoft Visual Studio 2015 et pour le SDK Microsoft Visual Studio 2015](/visualstudio/productinfo/2015-redistribution-vs). Pour plus d’informations sur les fichiers redistribuables, consultez [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md) et [Exemples de déploiement](deployment-examples.md).

Pour déployer des fichiers redistribuables Visual C++, vous pouvez utiliser les packages redistribuables Visual C++ (VCRedist\_x86.exe, VCRedist\_x64.exe ou VCRedist\_arm.exe) inclus dans Visual Studio. Dans Visual Studio 2017, ces fichiers sont disponibles dans le dossier Program Files[ (x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_, où _edition_ est l’édition de Visual Studio installée et _lib-version_ est la version des bibliothèques à redistribuer. Dans Visual Studio 2015, ces fichiers sont disponibles dans votre répertoire d’installation de Visual Studio sous Program Files [(x86)]\Microsoft Visual Studio *version*\VC\redist\\*locale*\\. Vous pouvez aussi utiliser des modules de fusion redistribuables (fichiers .msm) qui, dans Visual Studio 2017, sont disponibles dans le dossier Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_\\MergeModules\\. Dans Visual Studio 2015, ces fichiers sont disponibles dans Program Files [(x 86)]\Common Files\Merge Modules\\. Vous pouvez aussi installer directement les DLL Visual C++ redistribuables dans le *dossier local de l’application*, qui contient votre fichier d’application exécutable. Pour des raisons liées à la maintenance, il est déconseillé d'utiliser cet emplacement d'installation.

Les packages redistribuables Visual C++ installent et inscrivent toutes les bibliothèques Visual C++. Si vous en utilisez un, vous devez le définir de sorte qu'il s'exécute sur le système cible en tant que condition préalable à l'installation de l'application. Nous vous recommandons d'utiliser ces packages pour les déploiements car ils permettent une mise à jour automatique des bibliothèques Visual C++. Pour obtenir un exemple d’utilisation de ces packages, consultez [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide du package redistribuable Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Chaque package redistribuable Visual C++ vérifie l'existence d'une version plus récente sur l'ordinateur. Si une version plus récente est trouvée, le package n'est pas installé. Depuis Visual Studio 2015, les packages redistribuables affichent un message d'erreur indiquant que l'installation a échoué. Si un package est exécuté avec l’indicateur **/quiet**, aucun message d’erreur ne s’affiche. Dans les deux cas, une erreur est enregistrée par le programme d'installation de Microsoft, et un résultat d'erreur est retourné à l'appelant. À partir des packages de Visual Studio 2015, vous pouvez éviter cette erreur en recherchant dans le Registre si une version plus récente est installée. La version actuellement installée est stockée dans la clé HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_vs-version_\VC\Runtimes\\{x86|x64|ARM}, où _vs-version_ est le numéro de version de Visual Studio (14.0 pour Visual Studio 2015 et Visual Studio 2017, car le fichier redistribuable 2017 mis à jour est un fichier binaire compatible avec la version 2015) et où la clé est ARM, x86 ou x64, selon les versions de vcredist installées pour la plateforme. (Vous n’avez pas besoin de vérifier sous la sous-clé Wow6432Node, sauf si vous utilisez RegEdit pour afficher la version du package x86 installé sur une plateforme x64.) Le numéro de version est stocké dans la **version** de la valeur de chaîne REG_SZ, ainsi que dans l’ensemble de valeurs de REG_DWORD **majeures**, **Minor**, **bld**et **Rbld** . Pour éviter une erreur au moment de l’installation, vous devez ignorer l’installation du package redistribuable si la version actuellement installée est plus récente.

Si vous utilisez un module de fusion qui contient une DLL Visual C++, vous devez l’inclure dans le package Windows Installer (ou dans un package d’installation similaire) que vous utilisez pour déployer l’application. Pour plus d’informations, consultez [Redistribution à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md). Pour obtenir un exemple, consultez [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), qui montre aussi comment utiliser InstallShield Limited Edition pour créer un package d’installation.

## <a name="potential-run-time-errors"></a>Erreurs d'exécution potentielles

Si Windows ne peut pas trouver l’une des DLL de la bibliothèque redistribuable nécessaires pour votre application, un message semblable à celui-ci peut s’afficher : « Cette application n’a pas pu démarrer, car *bibliothèque*.dll est introuvable. La réinstallation de cette application peut corriger ce problème ».

Pour résoudre ce genre d’erreur, vérifiez que le programme d’installation de votre application se génère correctement et que les bibliothèques redistribuables sont déployées correctement sur le système cible. Pour plus d’informations, consultez [Fonctionnement des dépendances d’une application Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Redistribution à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md)|Décrit comment utiliser les modules de fusion redistribuables Visual C++ pour installer les bibliothèques Runtime Visual C++ sous forme de DLL partagées dans le dossier %windir%\system32\.|
|[Redistribution de contrôles ActiveX Visual C++](redistributing-visual-cpp-activex-controls.md)|Décrit comment redistribuer une application qui utilise les contrôles ActiveX.|
|[Redistribution de la bibliothèque MFC](redistributing-the-mfc-library.md)|Décrit comment redistribuer une application qui utilise MFC.|
|[Redistribution d’une application ATL](redistributing-an-atl-application.md)|Décrit comment redistribuer une application qui utilise ATL. Depuis Visual Studio 2012, aucune bibliothèque redistribuable pour ATL n'est requise.|
|[Exemples de déploiement](deployment-examples.md)|Fournit des liens vers des exemples qui illustrent le déploiement d'applications Visual C++.|
|[Déploiement d’applications de bureau](deploying-native-desktop-applications-visual-cpp.md)|Présente les concepts et les technologies de déploiement de Visual C++.|
