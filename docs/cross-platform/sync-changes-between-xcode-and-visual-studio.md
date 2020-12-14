---
description: 'En savoir plus sur : synchroniser les modifications entre Xcode et Visual Studio'
title: Synchroniser les changements entre Xcode et Visual Studio
ms.date: 10/17/2019
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.openlocfilehash: 60ce41e41f5b6a2a9f877501eaef0d84306dde07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229052"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchroniser les changements entre Xcode et Visual Studio

Les composants de développement mobile avec C++ dans Visual Studio incluent des fonctionnalités à distance pour synchroniser votre travail entre votre PC et votre Mac. Lorsque vos ordinateurs Visual Studio et Mac sont couplés, de nouvelles options sont disponibles pour les projets d’application iOS dans Visual Studio que vous pouvez utiliser pour ouvrir votre projet dans Xcode, déplacer votre code entre Xcode et Visual Studio, et nettoyer le répertoire de projet XCode temporaire.

Pour permettre l’utilisation des options de machine distante, votre projet doit être un projet d’application iOS, et Visual Studio doit être jumelé à votre Mac. Pour connaître les conditions préalables et obtenir des instructions sur la façon de coupler un Mac, consultez [installer et configurer des outils de génération à l’aide d’iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Menu Machine distante

Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur un projet d’application iOS pour afficher le menu contextuel. Sélectionnez l’élément **Machine distante** pour afficher les options distantes disponibles.

![Élément de menu machine distante dans Explorateur de solutions](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "Élément de menu machine distante dans Explorateur de solutions")

Ces commandes vous permettent d’ouvrir votre projet dans Xcode, de déplacer des modifications locales ou l’intégralité du projet entre Visual Studio et Xcode, et de nettoyer les fichiers temporaires sur l’ordinateur distant.

## <a name="open-in-xcode"></a>Ouvrir dans Xcode

Pour ouvrir le projet dans Xcode à partir de Visual Studio, dans le sous-menu **machine distante** , choisissez **ouvrir dans Xcode** pour ouvrir le projet sélectionné sur la machine distante couplée. Le `vcremote` serveur est utilisé pour ouvrir XCode sur votre Mac et accéder à un répertoire temporaire créé sur votre Mac qui contient une copie du projet. Visual Studio affiche une boîte de dialogue qui indique le répertoire temporaire utilisé pour le projet. Les actions effectuées sur la machine distante sont également affichées dans la fenêtre **Sortie** de Visual Studio. Pour les voir, vous devrez peut-être sélectionner **Machine distante Visual C++** dans la liste déroulante **Afficher la sortie à partir de** en haut de la fenêtre **Sortie**.

![La fenêtre sortie affiche les actions de l’ordinateur distant.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "La fenêtre sortie affiche les actions de l’ordinateur distant.")

Sur votre Mac, vous pouvez utiliser tous les outils Xcode pour modifier votre code et vos ressources, vos storyboards et vos actions. Dans Visual Studio, votre projet d’application iOS est annoté avec « ouvert dans Xcode » pour indiquer que des modifications peuvent être apportées sur l’ordinateur distant. Une fois vos modifications effectuées, vous pouvez utiliser les commandes Pull à partir de l’emplacement distant ou Pull incrémentiel à partir de l’emplacement distant pour copier ces changements dans votre projet Visual Studio.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>Push vers l’emplacement distant et Push incrémentiel vers l’emplacement distant

Si vous avez apporté des changements à votre projet d’application iOS dans Visual Studio, les commandes Push vers l’emplacement distant et Push incrémentiel vers l’emplacement distant peuvent vous permettre de déplacer les fichiers projet modifiés vers la machine distante jumelée. La commande Push vers l’emplacement distant copie tous les fichiers projet vers la machine distante. La commande Push incrémentiel vers l’emplacement distant ne copie que les fichiers modifiés vers la machine distante. Pour les grands projets avec de petits changements, la commande Push incrémentiel permet de gagner du temps et d’économiser de la bande passante.

Pour copier les fichiers projet vers votre Mac, dans Visual Studio, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, choisissez **Push vers l’emplacement distant** ou **Push incrémentiel vers l’emplacement distant** pour copier les fichiers projet de Visual Studio vers votre Mac.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Pull à partir de l’emplacement distant et Pull incrémentiel à partir de l’emplacement distant

Une fois que vous avez apporté des modifications à votre projet dans Xcode, replacez les modifications dans Visual Studio pour que les projets restent synchronisés.

Pour copier les fichiers projet depuis votre Mac, dans Visual Studio, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, choisissez **Pull à partir de l’emplacement distant** ou **Pull incrémentiel à partir de l’emplacement distant** pour copier les fichiers projet de votre Mac vers Visual Studio.

## <a name="clean-remote"></a>Nettoyer la machine distante

Vous pouvez utiliser la commande Nettoyer la machine distante pour supprimer les fichiers du répertoire de projet temporaire sur la machine distante. Le contenu du répertoire, notamment les fichiers sources ou les produits de build, est supprimé de votre Mac. Vérifiez que vous avez synchronisé tous les changements que vous souhaitez appliquer dans Visual Studio à l’aide des commandes Pull à partir de l’emplacement distant ou Pull incrémentiel à partir de l’emplacement distant, avant d’utiliser la commande Nettoyer la machine distante.

Pour nettoyer le répertoire de projet temporaire sur la machine distante, dans Visual Studio, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet Application iOS pour ouvrir le menu contextuel. Sélectionnez **Machine distante**, puis choisissez **Nettoyer la machine distante** pour supprimer les fichiers du répertoire de projet de votre Mac.
