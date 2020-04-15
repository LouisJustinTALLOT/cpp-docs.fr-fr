---
title: Déploiement de ClickOnce pour les applications Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4726fda8c5eca70ce7acde19f141a7c096395e95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316610"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Déploiement de ClickOnce pour les applications Visual C++

Visual Studio propose deux technologies différentes pour déployer les applications Windows : le déploiement ClickOnce ou le déploiement [Windows Installer](/windows/win32/Msi/windows-installer-portal).

## <a name="clickonce-deployment-in-c"></a>Déploiement ClickOnce en C++

L’environnement de développement Visual CMD ne prend pas directement en charge le déploiement de projets Visual Studio CMD avec ClickOnce, mais des outils sont disponibles pour l’utiliser.

> [!NOTE]
> Visual Studio prend en charge ClickOnce dans les environnements de développement Visual C# et Visual Basic. Si votre projet Visual Studio CMD est une dépendance d’un projet Visual CMD, vous pouvez publier l’application (y compris ses dépendances) en utilisant le déploiement ClickOnce à partir de l’environnement de développement Visual C.

Pour déployer une application Visual C++ à l’aide de ClickOnce, vous devez tout d’abord générer un [manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest) et un [manifeste de déploiement ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) à l’aide de [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) ou de sa version avec interface utilisateur graphique. Pour plus d’informations, consultez [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

Utilisez d’abord Mage.exe pour générer le manifeste d’application ; le fichier résultant portera l’extension .manifest. Utilisez ensuite Mage.exe pour générer le manifeste de déploiement ; le fichier résultant portera l'extension .application. Signez alors les manifestes.

Le manifeste d’application doit spécifier le processeur cible (**x86**, **x64** ou **ARM**). Pour plus d’informations sur ces options, consultez [Déploiement des prérequis pour les applications 64 bits](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications).

Par ailleurs, les noms de l'application et des manifestes de déploiement doivent être différents du nom de l'application C++. Cela évite le conflit entre le manifeste d'application, créé par Mage.exe, et le manifeste externe, qui fait partie de l'application C++.

Votre déploiement devra installer les bibliothèques Visual C++ dont votre application dépend. Pour déterminer les dépendances d'une application particulière, vous pouvez utiliser depends.exe ou l'utilitaire DUMPBIN avec l'option /DEPENDENTS. Pour plus d’informations sur les dépendances, consultez [Fonctionnement des dépendances d’une application Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Vous aurez peut-être besoin d’exécuter VCRedist.exe ; cet utilitaire installe des bibliothèques Visual C++ sur l’ordinateur cible.

Vous devrez peut-être également générer un programme d’amorçage (programme d’installation de composants prérequis) de votre application pour déployer des composants prérequis ; pour plus d’informations sur le programme d’amorçage, consultez [Création de packages de programme d’amorçage](/visualstudio/deployment/creating-bootstrapper-packages).

Pour une description plus détaillée de la technologie, consultez [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir un exemple détaillé de déploiement ClickOnce, consultez [Procédure pas à pas : déploiement manuel d’une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).

## <a name="see-also"></a>Voir aussi

[Mage.exe (Manifeste Génération et outil d’édition)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (Manifeste Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert.exe (outil de la création du certificat)](/windows/win32/SecCrypto/makecert)<br>
[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)<br>
[Déploiement d’applications, de services et de composants](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce Sécurité et déploiement](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Création de packages de programme d’amorçage](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[.NET Programmation avec CMD/CLI (Visual CMD)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
