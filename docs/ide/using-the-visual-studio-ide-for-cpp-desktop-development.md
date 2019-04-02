---
title: Utilisation de l'IDE de Visual Studio pour le développement de bureau C++
ms.date: 03/14/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 7417c46097b1f0c6282e3684a7556880c21be42a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773565"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Utilisation de l'IDE de Visual Studio pour le développement de bureau C++

L’environnement de développement intégré (IDE) Visual Studio offre un ensemble de fonctionnalités qui vous aident à gérer les projets de code, petits et grands, à écrire et refactoriser votre code ainsi qu’à détecter et corriger les erreurs à l’aide de l’analyse statique et de puissants outils de débogage. Cet ensemble d’articles est conçu pour vous guider tout au long de chaque étape nécessaire pour gérer vos projets, écrire, tester et déboguer votre code, puis le déployer sur un autre ordinateur.

## <a name="prerequisites"></a>Prérequis

Si vous n’avez pas encore installé Visual Studio, le moment est venu. Pour connaître les liens de téléchargement et suivre une procédure pas à pas rapide, consultez [Installer la prise en charge de C++ dans Visual Studio](../build/vscpp-step-0-installation.md). Pour plus d’informations sur l’installation de Visual Studio en général et obtenir des conseils de dépannage si un problème se produit, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio). Veillez à choisir la charge de travail **Développement Desktop en C++** pour inclure les compilateurs, outils et bibliothèques C++ quand vous installez Visual Studio, car ils ne sont pas installés par défaut.

Ces procédures pas à pas supposent que vous avez installé Visual Studio, ainsi que le langage Visual C++ et les composants nécessaires au développement Windows Desktop. Nous partons également du principe que vous comprenez les notions de base du langage C++. Si vous devez apprendre le langage C++, de nombreux livres et ressources web sont à votre disposition. Il est judicieux de commencer par la page [Prise en main](https://isocpp.org/get-started) du site web Standard C++ Foundation.

Si vous n’avez pas encore installé Visual Studio, le moment est venu.

**Installation de Visual Studio 2017**

Pour obtenir Visual Studio 2017, vous pouvez le télécharger depuis [Téléchargements de Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Veillez à inclure les outils de développement Visual C++ quand vous installez Visual Studio, car ceux-ci ne sont pas installés par défaut. Pour plus d’informations sur l’installation de Visual Studio, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio).

**Installation de Visual Studio 2015**

Pour installer Visual Studio 2015, accédez à [Télécharger d’anciennes versions de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Exécutez le programme d’installation, choisissez **Installation personnalisée**, puis le composant C++.

En règle générale, nous vous recommandons vivement d’utiliser Visual Studio 2017 même si vous avez besoin de compiler votre code en utilisant le compilateur de Visual Studio 2015. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](../porting/use-native-multi-targeting.md).

Une fois que vous avez terminé votre installation de Visual Studio, vous êtes prêt à continuer.

## <a name="get-started"></a>Prise en main

Pour commencer à utiliser l’IDE Visual Studio pour générer des applications C++, passez en revue chacune des rubriques ci-dessous dans l’ordre. Chacune d’elles s’appuie sur le travail effectué dans les rubriques précédentes :

- [Procédure pas à pas : utilisation de projets et de solutions (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Procédure pas à pas : Génération d’un projet (C++)](walkthrough-building-a-project-cpp.md)

- [Procédure pas à pas : Test d’un projet (C++)](walkthrough-testing-a-project-cpp.md)

- [Procédure pas à pas : Débogage d'un projet (C++)](walkthrough-debugging-a-project-cpp.md)

- [Procédure pas à pas : Déploiement de votre programme (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez terminé ces procédures pas à pas, vous êtes prêt à générer vos propres projets. Pour obtenir plus d’informations et de ressources pour le développement Visual C++, consultez [Visual C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

[Bien démarrer avec le développement dans Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)