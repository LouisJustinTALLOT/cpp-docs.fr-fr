---
title: Concepts relatifs au déploiement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16f135011f7b67debdf51f6ddbde00a79d130602
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199689"
---
# <a name="deployment-concepts"></a>Concepts relatifs au déploiement

Cette section présente les principales considérations relatives au déploiement d’applications C++.

## <a name="windows-installer-deployment-in-c"></a>Déploiement avec Windows Installer dans C++

Les projets Visual C++ utilisent en général pour le déploiement une installation traditionnelle avec Windows Installer. Pour préparer un déploiement Windows Installer, vous empaquetez votre application dans un fichier setup.exe et vous distribuez ce fichier, ainsi qu’un package d’installation (.msi). Les utilisateurs exécutent ensuite setup.exe pour installer votre application.

Vous empaquetez votre application en ajoutant un projet d’installation à votre solution ; lors de la génération, il crée le fichier d’installation et le package d’installation que vous distribuez aux utilisateurs. Pour plus d’informations, consultez [Choix d’une méthode de déploiement](../ide/choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Dépendances de bibliothèque

Quand une application C/C++ est générée avec des fonctionnalités fournies par les bibliothèques Visual C++, elle devient dépendante de la présence de ces bibliothèques lors de l’exécution. Pour que l’application puisse s’exécuter, elle doit être liée statiquement ou dynamiquement aux bibliothèques Visual C++ nécessaires. Si une application est liée dynamiquement à une bibliothèque Visual C++, quand elle s’exécute, la bibliothèque de liens doit être présente pour pouvoir être chargée. En revanche, si l’application est liée statiquement à une bibliothèque Visual C++, elle n’a pas besoin que les DLL correspondantes se trouvent sur l’ordinateur de l’utilisateur. Une liaison statique a cependant certains effets négatifs, comme l’augmentation de la taille des fichiers de l’application et une maintenance potentiellement plus difficile. Pour plus d’informations, consultez [Avantages de l’utilisation des DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Empaquetage et redistribution

Les bibliothèques Visual C++ sont empaquetées sous forme de DLL, et toutes les bibliothèques nécessaires pour les applications C/C++ sont installées par Visual Studio sur l’ordinateur du développeur. Cependant, lors du déploiement de votre application auprès de vos utilisateurs, il n’est pas possible dans la plupart des cas de leur demander d’installer Visual Studio pour pouvoir exécuter votre application. Il est important de pouvoir redistribuer seulement les composants de Visual C++ nécessaires pour que votre application s’exécute correctement.

Pour plus d’informations sur l’empaquetage et la redistribution, consultez les rubriques suivantes :

- [Détermination des DLL à redistribuer](../ide/determining-which-dlls-to-redistribute.md).

- [Choix d’une méthode de déploiement](../ide/choosing-a-deployment-method.md).

- [Déploiement de Universal CRT](universal-crt-deployment.md).

Pour obtenir des exemples de déploiement et des suggestions de résolution des problèmes, consultez :

- [Exemples de déploiement](../ide/deployment-examples.md).

- [Dépannage d’applications isolées et d’assemblys côte à côte C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Voir aussi

- [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Fonctionnement des dépendances d’une application Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Déploiement de Windows Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)
