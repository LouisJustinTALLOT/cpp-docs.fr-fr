---
title: Déploiement ClickOnce pour les applications Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e85ec0dfc011aab4d2b3ac835bbe71782b055000
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332323"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Déploiement ClickOnce pour les applications Visual C++
Visual Studio propose deux technologies différentes pour déployer les applications Windows : le déploiement ClickOnce ou le déploiement [Windows Installer](http://msdn.microsoft.com/library/cc185688).  
  
## <a name="clickonce-deployment-in-c"></a>Déploiement ClickOnce en C++  
 L’environnement de développement Visual C++ ne prend pas directement en charge le déploiement de projets Visual C++ avec ClickOnce, mais les outils pour l’utiliser sont disponibles.  
  
> [!NOTE]
>  Visual Studio prend en charge ClickOnce dans les environnements de développement Visual C# et Visual Basic. Si votre projet Visual C++ est une dépendance d’un projet Visual C#, vous pouvez publier l’application (dont ses dépendances) à l’aide du déploiement ClickOnce à partir de l’environnement de développement Visual C#.  
  
 Pour déployer une application Visual C++ à l’aide de ClickOnce, vous devez tout d’abord générer un [manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest) et un [manifeste de déploiement ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) à l’aide de [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) ou de sa version avec interface utilisateur graphique. Pour plus d’informations, consultez [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  

  
 Utilisez d’abord Mage.exe pour générer le manifeste d’application ; le fichier résultant portera l’extension .manifest. Utilisez ensuite Mage.exe pour générer le manifeste de déploiement ; le fichier résultant portera l’extension .application. Signez alors les manifestes.  
  
 Le manifeste d’application doit spécifier le processeur cible (**x86**, **x64** ou **ARM**). Pour plus d’informations sur ces options, consultez [Déploiement des prérequis pour les applications 64 bits](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications).  
  
 Par ailleurs, les noms de l'application et des manifestes de déploiement doivent être différents du nom de l'application C++. Cela évite le conflit entre le manifeste d'application, créé par Mage.exe, et le manifeste externe, qui fait partie de l'application C++.  
  
 Votre déploiement devra installer les bibliothèques Visual C++ dont votre application dépend. Pour déterminer les dépendances d'une application particulière, vous pouvez utiliser depends.exe ou l'utilitaire DUMPBIN avec l'option /DEPENDENTS. Pour plus d’informations sur les dépendances, consultez [Fonctionnement des dépendances d’une application Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Vous aurez peut-être besoin d’exécuter VCRedist.exe ; cet utilitaire installe des bibliothèques Visual C++ sur l’ordinateur cible.  
  
 Vous devrez peut-être également générer un programme d’amorçage (programme d’installation de composants prérequis) de votre application pour déployer des composants prérequis ; pour plus d’informations sur le programme d’amorçage, consultez [Création de packages de programme d’amorçage](/visualstudio/deployment/creating-bootstrapper-packages).  
  
 Pour une description plus détaillée de la technologie, consultez [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir un exemple détaillé de déploiement ClickOnce, consultez [Procédure pas à pas : déploiement manuel d’une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Makecert.exe (outil de la création du certificat)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Déploiement d’applications, de services et de composants](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Déploiement de Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Création de packages de programme d’amorçage](/visualstudio/deployment/creating-bootstrapper-packages)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)