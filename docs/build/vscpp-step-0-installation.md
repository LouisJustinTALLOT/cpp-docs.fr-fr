---
title: Installer la prise en charge de C++ dans Visual Studio
description: Installer la prise en charge de Visual Studio pour Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315145"
---
# <a name="install-c-support-in-visual-studio"></a>Installer la prise en charge de C++ dans Visual Studio

Si vous n’avez pas téléchargé et installé Visual Studio et les outils Visual C++ encore, voici comment commencer.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Installation de Visual Studio 2019

Bienvenue dans Visual Studio 2019 ! Dans cette version, vous pouvez facilement choisir et installer les fonctionnalités dont vous avez besoin uniquement. Et, en raison de son empreinte minimale réduite, elle s’installe rapidement avec un impact moindre sur le système.

> [!NOTE]
> Cette rubrique s’applique à l’installation de Visual Studio sur Windows. [Visual Studio Code](https://code.visualstudio.com/) est un environnement de développement multiplateforme et léger, qui s’exécute sur les systèmes Windows, Mac et Linux. Microsoft [C/C++ pour Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) extension prend en charge IntelliSense, le débogage de code de mise en forme, la saisie semi-automatique. Visual Studio pour Mac ne prend pas en charge Microsoft C++, mais prend en charge les langages .NET et le développement multiplateforme. Pour obtenir des instructions d’installation, consultez [installer Visual Studio pour Mac](/visualstudio/mac/installation/).

Vous voulez en savoir plus sur les autres nouveautés de cette version ? Consultez Visual Studio [notes de version](/visualstudio/releases/2019/release-notes/).

Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Étape 1 : Vérifier que votre ordinateur est prêt pour Visual Studio

Avant de commencer l’installation de Visual Studio :

1. Vérifiez la [configuration requise](/visualstudio/releases/2019/system-requirements). Celle-ci vous permet de savoir si votre ordinateur prend en charge Visual Studio 2019.

1. Appliquez les dernières mises à jour Windows Update. Ces mises à jour permettent de garantir que votre ordinateur dispose à la fois des dernières mises à jour de sécurité et des composants système obligatoires pour Visual Studio.

1. Redémarrez. Le redémarrage garantit que les éventuelles installations et mises à jour en attente n’entravent pas l’installation de Visual Studio.

1. Libérez de l’espace. Supprimez les fichiers et applications inutiles de %SystemDrive%, par exemple en exécutant l’application de nettoyage du disque.

Pour toute question sur l’exécution de versions antérieures de Visual Studio côte à côte avec Visual Studio 2019, consultez la page [Ciblage et compatibilité de la plateforme Visual Studio 2019](/visualstudio/releases/2019/compatibility/).

### <a name="step-2---download-visual-studio"></a>Étape 2 : Télécharger Visual Studio

Ensuite, téléchargez le fichier du programme d’amorçage de Visual Studio. Pour ce faire, choisissez le bouton Suivant, l’édition de Visual Studio souhaitée, **Enregistrer**, puis **Dossier ouvert**.

 > [!div class="button"]
 > [Télécharger Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Étape 3 : Installer le programme d’installation de Visual Studio

Exécutez le fichier du programme d’amorçage pour installer Visual Studio Installer. Ce nouveau programme d’installation léger inclut tout ce dont vous avez besoin pour installer et personnaliser Visual Studio.

1. Dans votre dossier **Téléchargements**, double-cliquez sur le programme d’amorçage correspondant ou similaire à l’un des fichiers suivants :

   * **vs_community.exe** pour Visual Studio Community
   * **vs_professional.exe** pour Visual Studio Professional
   * **vs_enterprise.exe** pour Visual Studio Enterprise

   Si vous recevez une notification du contrôle de compte d’utilisateur, choisissez **Oui**.

1. Vous devez accepter les [Termes du contrat de licence](https://visualstudio.microsoft.com/license-terms/) Microsoft et la [Déclaration de confidentialité](https://privacy.microsoft.com/privacystatement) Microsoft. Choisissez **Continuer**.

### <a name="step-4---choose-workloads"></a>Étape 4 : Choisir les charges de travail

Une fois le programme d’installation est installé, vous pouvez l’utiliser pour personnaliser votre installation en sélectionnant le *charges de travail*, ou une fonctionnalité de jeux, que vous souhaitez. Voici comment procéder.

1. Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.

   ![Visual Studio 2019 : Installer une charge de travail](../get-started/media/vs-installer-workloads.png)

   Pour la prise en charge C++ principal, choisissez la charge de travail « Développement Desktop en C++ ». Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.

   Charges de travail supplémentaires prennent en charge les autres types de développement C++. Par exemple, choisissez la charge de travail « Développement de plateforme Windows universelle » pour créer des applications qui utilisent le Runtime de Windows pour le Microsoft Store. Choisissez « Développement de jeux avec C++ » pour créer des jeux qui utilisent DirectX, Unreal et Cocos2d. Choisissez « Développement Linux en C++ » pour cibler les plateformes Linux, y compris le développement IoT.

   Le **détails de l’Installation** volet répertorie les composants inclus et facultatifs installés par chaque charge de travail. Vous pouvez sélectionner ou désélectionner les composants facultatifs dans cette liste. Par exemple, pour prendre en charge le développement en utilisant Visual Studio 2017 ou ensembles d’outils du compilateur 2015, choisissez le MSVC v141 ou les composants facultatifs de MSVC v140. Vous pouvez ajouter la prise en charge de MFC, l’extension de langage de Modules expérimentale, IncrediBuild et bien plus encore.

1. Une fois que vous choisissez les charges de travail et les composants facultatifs que vous souhaitez, choisissez **installer**.

    Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

> [!TIP]
> À tout moment après l’installation, vous pouvez installer les charges de travail ou les composants que vous n’avez pas installés au début. Si Visual Studio est ouvert, accédez à **Outils** > **Obtenir les outils et fonctionnalités** pour ouvrir Visual Studio Installer. Vous pouvez également ouvrir **Visual Studio Installer** à partir du menu Démarrer. À partir de là, vous pouvez choisir les charges de travail ou les composants à installer. Ensuite, choisissez **Modifier**.

## <a name="step-5---choose-individual-components-optional"></a>Étape 5 : Choisir des composants individuels (facultatif)

Si vous ne voulez pas utiliser la fonctionnalité Charges de travail pour personnaliser votre installation de Visual Studio, ou si vous voulez ajouter d’autres composants qui ne s’installent pas avec une charge de travail, installez ou ajoutez des composants individuels à partir de l’onglet **Composants individuels**. Choisissez ce que vous souhaitez, puis suivez les invites.

  ![Visual Studio 2019 - Installer des composants individuels](../get-started/media/vs-installer-individual-components.png "Installer des composants individuels de Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Étape 6 : Installer les modules linguistiques (facultatif)

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Pour installer Visual Studio dans la langue de votre choix, choisissez l’onglet **Modules linguistiques** dans Visual Studio Installer, puis suivez les invites.

  ![Visual Studio 2019 - Installer des modules linguistiques](../get-started/media/vs-installer-language-packs.png "Installer des modules linguistiques de Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Changer la langue du programme d’installation à partir de la ligne de commande

Une autre façon de changer la langue par défaut consiste à exécuter le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en utilisant la commande suivante : `vs_installer.exe --locale en-US`. Le programme d’installation enregistre ce paramètre lorsqu’elle est exécutée la prochaine fois. Le programme d’installation prend en charge les jetons de langue suivants : zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru et tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Étape 7 : Changer l’emplacement d’installation (facultatif)

Vous pouvez réduire l’empreinte de l’installation de Visual Studio sur votre lecteur système. Vous pouvez choisir de déplacer le cache de téléchargement, les composants partagés, les SDK et les outils vers d’autres lecteurs et de conserver Visual Studio sur le lecteur qui l’exécute le plus rapidement.

  ![Visual Studio 2019 - Changer l’emplacement d’installation](../get-started/media/vs-installer-installation-locations.png "Changer l’emplacement d’installation")

> [!IMPORTANT]
> Vous pouvez sélectionner un autre lecteur uniquement lors de la première installation de Visual Studio. Si vous l’avez déjà installé et que vous souhaitez changer de lecteur, vous devez désinstaller Visual Studio, puis le réinstaller.

## <a name="step-8---start-developing"></a>Étape 8 : Démarrer le développement

1. Une fois l’installation de Visual Studio terminée, choisissez le bouton **Lancer** pour commencer le développement avec Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

1. Dans la zone de recherche, entrez le type d’application à créer pour voir la liste des modèles disponibles. La liste des modèles varie selon les charges de travail que vous avez choisies lors de l’installation. Pour voir différents modèles, choisissez différentes charges de travail.

   Vous pouvez également filtrer votre recherche sur un langage de programmation spécifique à l’aide de la liste déroulante **Langage**. Vous pouvez aussi filtrer à l’aide de la liste **Plateforme** et de la liste **Type de projet**.

1. Visual Studio ouvre votre nouveau projet. Vous êtes prêt à coder !

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Installation de Visual Studio 2017

Dans Visual Studio 2017, il est facile de choisir et d’installer uniquement les fonctionnalités que vous avez besoin. Et, en raison de son empreinte minimale réduite, elle s’installe rapidement avec un impact moindre sur le système.

### <a name="prerequisites"></a>Prérequis

- Une connexion internet haut débit. Le programme d’installation de Visual Studio peut télécharger plusieurs gigaoctets de données.

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour la meilleure expérience de développement. Assurez-vous que les dernières mises à jour sont appliquées à votre système avant d’installer Visual Studio.

- Suffisamment d’espace disque libre. Visual Studio nécessite au moins 7 Go d’espace disque et peut prendre au moins 50 Go si de nombreuses options courantes sont installées. Nous vous recommandons de que vous l’installez sur votre lecteur C:.

Pour plus d’informations sur l’espace disque et la configuration requise du système d’exploitation, consultez [exigée Visual Studio produit famille](/visualstudio/productinfo/vs2017-system-requirements-vs). Le programme d’installation signale la quantité d’espace disque est nécessaire pour les options que vous sélectionnez.

### <a name="download-and-install"></a>Téléchargez et installez

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

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Installation de Visual Studio 2015

Pour installer Visual Studio 2015, accédez à [Télécharger d’anciennes versions de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Exécutez le programme d’installation, choisissez **Installation personnalisée**, puis le composant C++. Pour ajouter la prise en charge C++ à une installation existante de Visual Studio 2015, cliquez sur le bouton Démarrer de Windows et le type **Ajout/Suppression de programmes**. Ouvrez le programme à partir de la liste des résultats, puis recherchez votre installation de Visual Studio 2015 dans la liste des programmes installés. Double-cliquez dessus, puis choisissez **modifier** et sélectionnez les composants Visual C++ à installer.

En règle générale, nous vous recommandons vivement d’utiliser Visual Studio 2017 même si vous avez besoin de compiler votre code en utilisant le compilateur de Visual Studio 2015. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](../porting/use-native-multi-targeting.md).

::: moniker-end

Lorsque Visual Studio est en cours d’exécution, vous êtes prêt à continuer à l’étape suivante.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un projet C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
