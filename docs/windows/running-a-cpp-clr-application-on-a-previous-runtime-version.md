---
title: Exécution d’une application C++ -clr sur une version antérieure du runtime
ms.date: 11/04/2016
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
ms.openlocfilehash: 9b26439d389cb4035541cedde8a5b5cf50682098
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388357"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Exécution d'une application C++ /clr sur une version antérieure du runtime

Sauf indication contraire, une application C++ .NET Framework est générée pour s’exécuter sur la version du Common Language Runtime (CLR) que le compilateur utilise pour générer l’application. Toutefois, il est possible d’exécuter une application .exe qui est créée pour une version du runtime sur n’importe quelle autre version qui fournit la fonctionnalité requise.

Pour ce faire, fournissez un fichier app.config qui contient les informations de version du runtime dans la balise `supportedRuntime`.

Au moment de l’exécution, le fichier app.config doit avoir un nom sous la forme *filename.ext*.config, où *filename.ext* est le nom du fichier exécutable qui a démarré l’application, et doit se trouver dans le même répertoire que le fichier exécutable. Par exemple, si votre application est nommée TestApp.exe, le fichier app.config est nommé TestApp.exe.config.

Si vous spécifiez plusieurs versions du runtime et que l’application s’exécute sur un ordinateur sur lequel plusieurs versions du runtime sont installées, l’application utilise la première version spécifiée dans le fichier de configuration.

## <a name="see-also"></a>Voir aussi

[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)
