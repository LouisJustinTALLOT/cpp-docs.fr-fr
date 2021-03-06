---
description: 'En savoir plus sur : déploiement d’applications de bureau natives (Visual C++)'
title: Déploiement des applications de bureau natives (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.topic: overview
ms.openlocfilehash: c3da460266eb630e7ac243f523fa6e89a79fa1f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329441"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Déploiement des applications de bureau natives (Visual C++)

Un déploiement est le processus par lequel vous distribuez une application ou un composant terminé pour l’installer sur d’autres ordinateurs. La planification du déploiement commence quand l’application est créée sur l’ordinateur d’un développeur. Un déploiement se termine quand l’application est installée et prête à être exécutée sur l’ordinateur d’un utilisateur.

Visual Studio fournit différentes technologies pour déployer des applications Windows. Il s’agit notamment du déploiement ClickOnce et du déploiement Windows Installer.

- ClickOnce peut servir à déployer des applications C++ qui ciblent le CLR (Common Language Runtime) : assemblys mixtes, purs et vérifiables. Même si vous pouvez utiliser Windows Installer pour déployer une application managée, nous vous recommandons d’utiliser ClickOnce, car il tire parti des fonctionnalités de sécurité du .NET Framework, comme la signature de manifeste. ClickOnce ne prend pas en charge le déploiement d’applications C++ natives. Pour plus d’informations, consultez [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

- La technologie Windows Installer peut être utilisée pour déployer des applications C++ natives ou des applications C++ qui ciblent le CLR.

Les articles de cette section de la documentation expliquent comment vous assurer qu’une application Visual C++ native s’exécute sur tout ordinateur qui fournit une plateforme cible prise en charge, quels fichiers vous devez inclure dans un package d’installation et les méthodes recommandées pour redistribuer les composants dont votre application dépend.

## <a name="in-this-section"></a>Dans cette section

- [Déploiement dans Visual C++](deployment-in-visual-cpp.md)

- [Concepts relatifs au déploiement](deployment-concepts.md)

- [Fonctionnement des dépendances d'une application Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md)

- [Choix d’une méthode de déploiement](choosing-a-deployment-method.md)

- [Déploiement du CRT universel](universal-crt-deployment.md).

- [Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md)

- [Exemples de déploiement](deployment-examples.md)

- [Redistribution d’applications clientes web](redistributing-web-client-applications.md)

- [Déploiement ClickOnce pour les applications Visual C++](clickonce-deployment-for-visual-cpp-applications.md)

- [Exécution d'une application C++ /clr sur une version antérieure du runtime](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Sections connexes

- [Génération d’applications isolées C/C++ et d’assemblys côte à côte](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Déploiement](/dotnet/framework/deployment/index)

- [Résolution des problèmes d’applications isolées C/C++ et d’assemblys côte à côte](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
