---
title: Choix d'une méthode de déploiement
ms.date: 03/14/2019
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
ms.openlocfilehash: 633b76458fdc24ef9ba551d8209c5c99720df37e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377404"
---
# <a name="choosing-a-deployment-method"></a>Choix d'une méthode de déploiement

À moins que votre application Visual C++ soit autonome et déployable à l’aide d’une commande de copie, nous vous recommandons d’utiliser Windows Installer pour le déploiement. Windows Installer prend en charge l'installation, la réparation, et la désinstallation. Il prend également en charge la mise à jour atomique des fichiers, des dépendances et des entrées de registre de l'application.

> [!NOTE]
> Le déploiement [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) des applications natives Visual C++ est certes possible dans Visual Studio, mais il nécessite des étapes supplémentaires. Pour plus d’informations, consultez [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Les bibliothèques Visual C++ sont des DLL partagées

Les bibliothèques Visual C++ étant installées dans le répertoire %windir%\system32\ par le programme d'installation de Visual Studio, toute application Visual C++ que vous développerez avec des dépendances à celles-ci fonctionnera comme prévu. Toutefois, avant de déployer l'application sur des ordinateurs où Visual Studio peut être absent, nous vous recommandons de vérifier que les bibliothèques sont installées sur ceux-ci en même temps que l'application.

## <a name="redistributing-visual-c-libraries"></a>Redistribution des bibliothèques Visual C++

Dans vos déploiements, vous pouvez redistribuer n'importe quelle version d'une bibliothèque Visual C++ dont la redistribution est autorisée. Voici trois manières de les déployer :

- Le déploiement centralisé, à l’aide de packages redistribuables, qui installe les bibliothèques Visual C++ sous forme de DLL partagées dans %windir%\system32\\. (L’installation dans ce dossier nécessite des droits d’administrateur.) Vous pouvez créer un script ou un programme de configuration qui exécute le paquet redistributable avant d’installer votre application sur l’ordinateur cible. Il existe des packages redistribuables pour les plateformes x86, x64 et ARM (VCRedist_x86.exe, VCRedist_x64.exe, ou VCRedist_arm.exe). Visual Studio inclut ces packages dans %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Vous pouvez également les télécharger à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download). (Utilisez la zone de recherche dans le Centre de téléchargement pour rechercher le package redistribuable « Visual C++ Redistributable Package *version et mise à jour de Visual Studio* » qui correspond à votre application. Par exemple, si vous avez utilisé la mise à jour 3 de Visual Studio 2015 pour créer votre application, recherchez la mise à jour 3 du « Paquet Redistributable Visual CMD 2015 ). Pour plus d’informations sur la façon d’utiliser un paquet redistributable, voir [Procédure pas à pas : Déployer une application visuelle CMD en utilisant le paquet redistributable Visual CMMD](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Le déploiement centralisé à l’aide des modules de fusion, chacun installant une bibliothèque Visual C++ particulière sous forme de DLL partagée dans %windir%\system32\\. (L’installation à ce dossier nécessite des droits d’administrateur.) Les modules de fusion font partie du fichier d’installateur .msi pour votre application. Les modules de fusion redistribuables Visual C++ sont inclus dans Visual Studio, dans \Program Files (x86)\Common Files\Merge Modules\\. Pour plus d’informations, consultez [Redistribution à l’aide de modules de fusion](redistributing-components-by-using-merge-modules.md).

- Le déploiement local, qui consiste à copier certaines DLL Visual C++ de votre installation Visual Studio, généralement dans \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\, et à les installer ensuite sur les ordinateurs cibles dans le même dossier que le fichier exécutable de l’application. Vous pouvez utiliser cette méthode de déploiement pour permettre l'installation par des utilisateurs ne possédant pas de droits d'administrateur, ou pour les applications exécutables à partir d'un partage réseau.

Quand un déploiement utilise des modules de fusion redistribuables et que l’installation est exécutée par un utilisateur sans droits d’administrateur, les DLL Visual C++ ne sont pas installées et l’application ne s’exécute pas. De plus, les programmes d'installation d'application, générés avec des modules de fusion permettant l'installation par des utilisateurs individuels, installent les bibliothèques dans un emplacement partagé qui affecte tous les utilisateurs du système. Vous pouvez utiliser le déploiement local pour installer les DLL Visual C++ nécessaires dans le répertoire d’application d’un utilisateur particulier sans affecter d’autres utilisateurs ni exiger des droits d’administrateur. En raison de problèmes de maintenance possibles, nous déconseillons le déploiement local des DLL redistribuables Visual C++.

Une redistribution incorrecte des bibliothèques Visual C++ peut provoquer des erreurs pendant l'exécution d'une application qui en dépend. Lorsque le système d’exploitation charge l’application, il utilise l’ordre de recherche décrit dans [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="dynamic-linking-is-better-than-static-linking"></a>La liaison dynamique est supérieure à la liaison statique

Nous vous recommandons d’éviter la liaison statique quand vous redistribuez des bibliothèques Visual C++. Bien que la liaison statique n’améliore presque jamais de manière significative les performances des applications, elle en rend la maintenance presque toujours plus coûteuse. Par exemple, considérez une application statiquement liée à une bibliothèque en cours de mise à jour avec des améliorations de sécurité. Celle-ci ne pourra pas bénéficier des ces améliorations à moins d'être recompilée et redéployée. À la place, nous vous recommandons de lier vos applications dynamiquement aux bibliothèques desquelles elles dépendent, de manière à en permettre la mise à jour dans tous les emplacements où elles sont déployées.

## <a name="see-also"></a>Voir aussi

[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce Sécurité et déploiement](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Exemples de déploiement](deployment-examples.md)
