---
title: Installer la prise en charge C++ dans Visual Studio | Documents Microsoft
description: Installer la prise en charge de Visual Studio pour Visual C++
ms.custom: mvc
ms.date: 06/21/2018
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5807110caf730c72d93de7e1265199b63f1d6bff
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322483"
---
# <a name="install-c-support-in-visual-studio"></a>Installer la prise en charge C++ dans Visual Studio

Si vous n’avez pas encore téléchargé et encore installé Visual Studio et les outils Visual C++, voici comment commencer.

## <a name="prerequisites"></a>Prérequis

- Une connexion internet haut débit. Le programme d’installation de Visual Studio peut télécharger plusieurs gigaoctets de données.

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous vous recommandons de Windows 10 pour la meilleure expérience de développement. Assurez-vous que les dernières mises à jour sont appliquées à votre système avant d’installer Visual Studio.

- Suffisamment d’espace disque libre. Visual Studio requiert au moins 7 Go d’espace disque et peut prendre au moins 50 Go si de nombreuses options courantes sont installées. Nous vous recommandons de que vous l’installez sur votre lecteur C:.

Pour plus d’informations sur l’espace disque et la configuration requise du système d’exploitation, consultez [Visual Studio produit famille requise](/visualstudio/productinfo/vs2017-system-requirements-vs). Le programme d’installation signale que la quantité d’espace disque est requis pour les options que vous sélectionnez.

## <a name="installation"></a>Installation

1. Téléchargez le programme d’installation de Visual Studio 2017 la plus récente pour Windows.

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Installer Visual Studio 2017 Community</a>

   >[!Tip]
   > L’édition Community est destinée aux développeurs individuels, à l’apprentissage en classe, à la recherche académique et au développement open source. Pour les autres utilisations, installez <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Professional</a> ou <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Enterprise</a>.

1. Recherchez le fichier de programme d’installation vous avez téléchargé et exécutez-le. Il peut s’afficher dans votre navigateur, ou il peut s’avérer dans votre dossier Téléchargements. Le programme d’installation a besoin de privilèges d’administrateur pour s’exécuter. Vous pouvez voir un **contrôle de compte d’utilisateur** boîte de dialogue vous demandant d’accorder l’autorisation pour le programme d’installation permettent d’apporter des modifications à votre système ; choisissez **Oui**. Si vous rencontrez des problèmes, recherchez le fichier téléchargé dans l’Explorateur de fichiers, avec le bouton droit sur l’icône de programme d’installation et choisissez **exécuter en tant qu’administrateur** dans le menu contextuel.

   ![Exécutez le programme d’installation de Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "exécuter le programme d’installation de Visual Studio")

1. Le programme d’installation vous présente une liste de charges de travail, qui sont des groupes d’options connexes pour des types de développement spécifiques. Prise en charge de C++ fait désormais partie de charges de travail facultatives qui ne sont pas installés par défaut.

   ![Développement de bureau avec C++](../build/media/desktop-development-with-cpp.png "bureau développement avec C++")

    Pour C++, sélectionnez le **bureau développement avec C++** la charge de travail, puis choisissez **installer**.

   ![Installer le développement de bureau avec une charge de travail C++](../build/media/vscpp-concierge-choose-workload.gif "installer le développement de bureau avec une charge de travail de C++")

1. Lorsque l’installation est terminée, choisissez le **lancer** bouton à démarrer Visual Studio.

   La première fois que vous exécutez Visual Studio, vous êtes invité à vous connecter à un Account Microsoft. Si vous n’en avez pas, vous pouvez créer un gratuitement. Vous devez également choisir un thème. Ne vous inquiétez pas, vous pouvez modifier ultérieurement si vous le souhaitez. 

   Il peut prendre Visual Studio plusieurs minutes pour se préparer à utiliser la première fois que vous exécutez. Voici à quoi elle ressemble dans une rapide séquentiel :

   ![Visual Studio 2017 connectez-vous](../build/media/vscpp-quickstart-first-run.gif "Visual Studio 2017 connectez-vous")

   Visual Studio démarre beaucoup plus rapidement lorsque vous l’exécutez à nouveau.

1. Lorsque Visual Studio s’ouvre, vérifiez si l’icône d’indicateur dans la barre de titre est mis en surbrillance :

   ![Indicateur de notification Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "indicateur de notification de Visual Studio 2017")

   Si elle est mise en surbrillance, sélectionnez-le pour ouvrir la **Notifications** fenêtre. Si des mises à jour sont disponibles pour Visual Studio, nous vous recommandons de que les installer maintenant. Une fois l’installation terminée, redémarrez Visual Studio.

Lorsque Visual Studio est en cours d’exécution, vous êtes prêt à continuer à l’étape suivante.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un projet C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
