---
title: Installer la prise en charge C++ dans Visual Studio 2017
description: Installer la prise en charge de Visual Studio pour Visual C++
ms.custom: mvc
ms.date: 11/19/2018
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 6c5adac9bb31287693b7d53c1fa8ff10263f4367
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815851"
---
# <a name="install-c-support-in-visual-studio"></a>Installer la prise en charge C++ dans Visual Studio

Si vous n’avez pas téléchargé et installé Visual Studio 2017 et les outils Visual C++ encore, voici comment commencer.

## <a name="prerequisites"></a>Prérequis

- Une connexion internet haut débit. Le programme d’installation de Visual Studio peut télécharger plusieurs gigaoctets de données.

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour la meilleure expérience de développement. Assurez-vous que les dernières mises à jour sont appliquées à votre système avant d’installer Visual Studio.

- Suffisamment d’espace disque libre. Visual Studio nécessite au moins 7 Go d’espace disque et peut prendre au moins 50 Go si de nombreuses options courantes sont installées. Nous vous recommandons de que vous l’installez sur votre lecteur C:.

Pour plus d’informations sur l’espace disque et la configuration requise du système d’exploitation, consultez [exigée Visual Studio produit famille](/visualstudio/productinfo/vs2017-system-requirements-vs). Le programme d’installation signale la quantité d’espace disque est nécessaire pour les options que vous sélectionnez.

## <a name="visual-studio-2015-installation"></a>Installation de Visual Studio 2015

Pour installer Visual Studio 2015, accédez à [Télécharger d’anciennes versions de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Exécutez le programme d’installation, choisissez **Installation personnalisée**, puis le composant C++. Pour ajouter la prise en charge C++ à une installation existante de Visual Studio 2015, cliquez sur le bouton Démarrer de Windows et le type **Ajout/Suppression de programmes**. Ouvrez le programme à partir de la liste des résultats, puis recherchez votre installation de Visual Studio 2015 dans la liste des programmes installés. Double-cliquez dessus, puis choisissez **modifier** et sélectionnez les composants Visual C++ à installer.

En règle générale, nous vous recommandons vivement d’utiliser Visual Studio 2017 même si vous avez besoin de compiler votre code en utilisant le compilateur de Visual Studio 2015. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](../porting/use-native-multi-targeting.md).

## <a name="visual-studio-2017-installation"></a>Installation de Visual Studio 2017

1. Téléchargez le programme d’installation de Visual Studio 2017 la plus récente pour Windows.

   > [!div class="nextstepaction"]
   > [Installer Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > L’édition Community est destinée aux développeurs individuels, à l’apprentissage en classe, à la recherche académique et au développement open source. Pour les autres utilisations, installez [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ou [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Recherchez le fichier de programme d’installation téléchargé et l’exécuter. Il peut s’afficher dans votre navigateur, ou il peut s’avérer dans votre dossier Téléchargements. Le programme d’installation a besoin de privilèges d’administrateur pour s’exécuter. Vous pouvez voir un **contrôle de compte d’utilisateur** boîte de dialogue vous demandant d’accorder l’autorisation pour vous permettre du programme d’installation apporter des modifications à votre système ; choisissez **Oui**. Si vous rencontrez des problèmes, recherchez le fichier téléchargé dans l’Explorateur de fichiers, avec le bouton droit sur l’icône de programme d’installation et choisissez **exécuter en tant qu’administrateur** dans le menu contextuel.

   ![Téléchargez et installez Visual Studio Installer](media/vscpp-concierge-run-installer.gif "télécharger et installer Visual Studio Installer")

1. Le programme d’installation vous présente une liste de charges de travail, qui sont des groupes d’options connexes pour des types de développement spécifiques. Prise en charge de C++ fait désormais partie des charges de travail facultatifs qui ne sont pas installés par défaut.

   ![Développement Desktop en charge de travail C++](media/desktop-development-with-cpp.png "développement Desktop en C++")

   Pour C++, sélectionnez le **développement Desktop en C++** charge de travail, puis choisissez **installer**.

   ![Installez le développement bureautique avec la charge de travail C++](media/vscpp-concierge-choose-workload.gif "installez le développement bureautique avec la charge de travail C++")

1. Lorsque l’installation est terminée, choisissez le **lancer** bouton pour démarrer Visual Studio.

   La première fois que vous exécutez Visual Studio, vous êtes invité à vous connecter avec un Account Microsoft. Si vous n’en avez pas, vous pouvez créer un gratuitement. Vous devez également choisir un thème. Ne vous inquiétez pas, vous pouvez modifier ultérieurement si vous le souhaitez.

   Il faudra encore Visual Studio plusieurs minutes pour se préparer à utilisent la première fois que vous l’exécutez. Voici ce que cela donne dans un rapide séquentiel :

   ![Visual Studio 2017 connectez-vous](media/vscpp-quickstart-first-run.gif "connecter Visual Studio 2017")

   Visual Studio démarre beaucoup plus rapidement lorsque vous l’exécutez à nouveau.

1. Lorsque Visual Studio s’ouvre, vérifiez si l’icône d’indicateur dans la barre de titre est mis en surbrillance :

   ![Indicateur de notification Visual Studio 2017](media/vscpp-first-start-page-flag.png "indicateur de notification de Visual Studio 2017")

   Si elle est mise en surbrillance, sélectionnez-la pour ouvrir le **Notifications** fenêtre. Si les mises à jour sont disponibles pour Visual Studio, nous vous recommandons de que les installer maintenant. Une fois que l’installation est terminée, redémarrez Visual Studio.

Lorsque Visual Studio est en cours d’exécution, vous êtes prêt à continuer à l’étape suivante.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un projet C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
