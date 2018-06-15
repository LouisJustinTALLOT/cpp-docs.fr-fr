---
title: Exécution d’une application C++ /clr sur une version antérieure du runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8e76930eb9191d27085d92a9d3a678812715fc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323613"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Exécution d'une application C++ /clr sur une version antérieure du runtime
Sauf indication contraire, une application C++ .NET Framework est générée pour s’exécuter sur la version du Common Language Runtime (CLR) que le compilateur utilise pour générer l’application. Toutefois, il est possible d’exécuter une application .exe qui est créée pour une version du runtime sur n’importe quelle autre version qui fournit la fonctionnalité requise.  
  
 Pour ce faire, fournissez un fichier app.config qui contient les informations de version du runtime dans la balise `supportedRuntime`.  
  
 Au moment de l’exécution, le fichier app.config doit avoir un nom sous la forme *filename.ext*.config, où *filename.ext* est le nom du fichier exécutable qui a démarré l’application, et doit se trouver dans le même répertoire que le fichier exécutable. Par exemple, si votre application est nommée TestApp.exe, le fichier app.config est nommé TestApp.exe.config.  
  
 Si vous spécifiez plusieurs versions du runtime et que l’application s’exécute sur un ordinateur sur lequel plusieurs versions du runtime sont installées, l’application utilise la première version spécifiée dans le fichier de configuration.  
  
 Pour plus d’informations, consultez [Guide pratique pour configurer une application pour cibler une version du .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Pour une exécution sur la version 1.0 ou 1.1 du CLR, une application générée par le compilateur Visual C++ doit être compilée avec [/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)