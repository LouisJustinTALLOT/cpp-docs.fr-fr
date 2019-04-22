---
title: Déploiement dans Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 8dccf581cff88dc2e8c4a889bed8b47fc140eb7c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786277"
---
# <a name="deployment-in-visual-c"></a>Déploiement dans Visual C++

L’installation de votre application sur un ordinateur autre que votre ordinateur de développement est appelée *déploiement*. Quand vous déployez une application Visual C++ sur un autre ordinateur, vous devez installer l’application et tous les fichiers bibliothèques dont elle dépend. Visual Studio offre trois manières de déployer les bibliothèques Visual C++ avec votre application : *déploiement centralisé*, *déploiement local* et *liaison statique*. Le déploiement central place les fichiers bibliothèques sous le répertoire Windows, où le service Windows Update peut les mettre à jour automatiquement. Le déploiement local place les fichiers bibliothèques dans le même répertoire que votre application. Vous devez redéployer vous-même les bibliothèques déployées localement pour les mettre à jour. La liaison statique lie le code des bibliothèques dans votre application. Quand vous utilisez la liaison statique, vous devez recompiler et redéployer votre application pour bénéficier des mises à jour des bibliothèques.

Dans Visual Studio 2015, la bibliothèque Microsoft C Runtime a été refactorisée en composants de bibliothèque locale spécifique à une version et en une nouvelle bibliothèque Universal Runtime C qui fait désormais partie de Windows. Pour plus d’informations sur le déploiement de Universal CRT, consultez [Déploiement de Universal CRT](universal-crt-deployment.md).

## <a name="central-deployment"></a>Déploiement central

Dans un déploiement central, les fichiers DLL de bibliothèque sont installés dans le répertoire Windows\System32 ou, pour les fichiers de bibliothèque 32 bits sur les systèmes x64, dans le répertoire Windows\SysWow64. Microsoft met automatiquement à jour les bibliothèques qui sont déployées de manière centralisée. Pour les bibliothèques Visual C++ déployées localement ou liées statiquement, vous devez fournir les mises à jour.

Pour déployer de façon centralisée des bibliothèques Visual C++, vous pouvez utiliser une de ces deux sources pour les fichiers à installer :

- Les fichiers du *package redistribuable*, qui sont des exécutables autonomes de ligne de commande contenant toutes les bibliothèques redistribuables Visual C++ sous une forme compressée.

- Les *modules de fusion redistribuables* (fichiers .msm), que vous pouvez utiliser pour déployer des bibliothèques spécifiques et que vous incluez dans le fichier Windows Installer (.msi) de votre application.

Un fichier de package redistribuable installe toutes les bibliothèques Visual C++ pour une architecture système particulière. Par exemple, si votre application est générée pour x64, vous pouvez utiliser le package redistribuable vcredist_x64.exe pour installer toutes les bibliothèques Visual C++ utilisées par votre application. Vous pouvez faire en sorte que votre programme d’installation d’application exécute le package redistribuable comme prérequis à l’installation de l’application.

Un module de fusion permet l’inclusion de la logique d’installation pour une bibliothèque Visual C++ spécifique dans un fichier d’installation d’application Windows Installer. Vous pouvez inclure exactement les modules de fusion nécessaires à votre application. Utilisez les modules de fusion quand vous avez besoin de réduire la taille des fichiers binaires de votre déploiement.

Étant donné que le déploiement central avec un package redistribuable ou des modules de fusion permet à Windows Update de mettre à jour automatiquement les bibliothèques Visual C++, nous vous recommandons d’utiliser les DLL des bibliothèques dans votre application au lieu de bibliothèques statiques, et d’utiliser le déploiement central au lieu du déploiement local.

## <a name="local-deployment"></a>Déploiement local

Dans un déploiement local, les fichiers bibliothèques sont installés dans le dossier de votre application avec le fichier exécutable. Vous pouvez installer différentes versions des bibliothèques redistribuables Visual C++ dans le même dossier, car le nom de fichier de chaque version inclut son numéro de version. Par exemple, la version 12 de la bibliothèque de runtime C++ est msvcp120.dll et la version 14 est msvcp140.dll.

Une bibliothèque peut être répartie entre plusieurs DLL, appelées *bibliothèques dot*. Par exemple, certaines fonctionnalités de la bibliothèque standard publiée dans Visual Studio 2017 version 15.6 ont été ajoutées à msvcp140_1.dll de façon à conserver la compatibilité ABI de msvcp140.dll. Si vous utilisez Visual Studio 2017 version 15.6 (ensemble d’outils 14.13) ou un ensemble d’outils ultérieur de Visual Studio 2017, il peut être nécessaire de déployer localement ces bibliothèques dot ainsi que la bibliothèque principale. Ces bibliothèques dot distinctes sont ensuite ajoutées dans la version majeure suivante de la bibliothèque de base quand l’ABI change.

Étant donné que Microsoft ne peut pas mettre à jour automatiquement les bibliothèques Visual C++ déployées localement, nous ne recommandons pas le déploiement local de celles-ci. Si vous décidez de recourir au déploiement local des bibliothèques redistribuables, nous vous recommandons d'appliquer votre propre méthode de mise à jour automatique des bibliothèques déployées localement.

## <a name="static-linking"></a>Liaison statique

En plus des bibliothèques liées dynamiquement, Visual Studio fournit la plupart de ses bibliothèques sous forme de bibliothèques statiques. Vous pouvez lier statiquement une bibliothèque statique à votre application, c’est-à-dire lier le code objet de la bibliothèque directement dans l’application. Ceci crée un seul fichier binaire sans une dépendance de DLL : vous n’avez donc pas à déployer les fichiers de bibliothèque Visual C++ séparément. Nous ne recommandons cependant pas cette approche, car les bibliothèques liées statiquement ne peuvent pas être mises à jour sur place. Si vous utilisez la liaison statique et souhaitez mettre à jour une bibliothèque liée, vous devez recompiler et redéployer votre application.

## <a name="troubleshooting-deployment-issues"></a>Résolution des problèmes de déploiement

L’ordre de chargement des bibliothèques Visual C++ dépend du système. Pour diagnostiquer des problèmes liés au chargeur, utilisez depends.exe ou where.exe. Pour plus d’informations, consultez [Dynamic-Link Library Search Order (Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Voir aussi

- [Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)
- [Déploiement de Universal CRT](universal-crt-deployment.md)
