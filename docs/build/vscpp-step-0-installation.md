---
title: Installer la prise en charge de C++ dans Visual Studio
description: Installer le support Visual Studio pour Visual C
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335366"
---
# <a name="install-c-support-in-visual-studio"></a>Installer la prise en charge de C++ dans Visual Studio

Si vous n’avez pas encore téléchargé et installé Visual Studio et les outils Visual CMD, voici comment commencer.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Installation de Visual Studio 2019

Bienvenue dans Visual Studio 2019 ! Dans cette version, vous pouvez facilement choisir et installer les fonctionnalités dont vous avez besoin uniquement. Et, en raison de son empreinte minimale réduite, elle s’installe rapidement avec un impact moindre sur le système.

> [!NOTE]
> Ce sujet s’applique à l’installation de Visual Studio sur Windows. [Visual Studio Code](https://code.visualstudio.com/) est un environnement de développement léger et multiplateforme qui s’exécute sur les systèmes Windows, Mac et Linux. L’extension Microsoft [C/CMD pour Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) prend en charge IntelliSense, débogage, formatage de code, auto-achèvement. Visual Studio pour Mac ne prend pas en charge Microsoft C, mais prend en charge les langues .NET et le développement de plateformes croisées. Pour les instructions d’installation, voir [Installer Visual Studio pour Mac](/visualstudio/mac/installation/).

Vous voulez en savoir plus sur les autres nouveautés de cette version ? Voir les [notes de sortie](/visualstudio/releases/2019/release-notes/)visual Studio .

Prêt pour l’installation ? Nous allons vous guider dans les étapes de l’installation.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Étape 1 : Vérifier que votre ordinateur est prêt pour Visual Studio

Avant de commencer l’installation de Visual Studio :

1. Vérifiez la [configuration requise](/visualstudio/releases/2019/system-requirements). Celle-ci vous permet de savoir si votre ordinateur prend en charge Visual Studio 2019.

1. Appliquez les dernières mises à jour Windows Update. Ces mises à jour permettent de garantir que votre ordinateur dispose à la fois des dernières mises à jour de sécurité et des composants système obligatoires pour Visual Studio.

1. Redémarrage. Le redémarrage garantit que les éventuelles installations et mises à jour en attente n’entravent pas l’installation de Visual Studio.

1. Libérez de l’espace. Supprimez les fichiers et applications inutiles de %SystemDrive%, par exemple en exécutant l’application de nettoyage du disque.

Pour toute question sur l’exécution de versions antérieures de Visual Studio côte à côte avec Visual Studio 2019, consultez la page [Ciblage et compatibilité de la plateforme Visual Studio 2019](/visualstudio/releases/2019/compatibility/).

### <a name="step-2---download-visual-studio"></a>Étape 2 : Télécharger Visual Studio

Ensuite, téléchargez le fichier du programme d’amorçage de Visual Studio. Pour ce faire, choisissez le bouton Suivant, l’édition de Visual Studio souhaitée, **Enregistrer**, puis **Dossier ouvert**.

 > [!div class="button"]
 > [Télécharger Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Étape 3 : Installer le programme d’installation de Visual Studio

Exécutez le fichier du programme d’amorçage pour installer Visual Studio Installer. Ce nouveau programme d’installation léger inclut tout ce dont vous avez besoin pour installer et personnaliser Visual Studio.

1. Dans votre dossier **Téléchargements**, double-cliquez sur le programme d’amorçage correspondant ou similaire à l’un des fichiers suivants :

   - **vs_community.exe** pour Visual Studio Community
   - **vs_professional.exe** pour Visual Studio Professional
   - **vs_enterprise.exe** pour Visual Studio Enterprise

   Si vous recevez une notification du contrôle de compte d’utilisateur, choisissez **Oui**.

1. Nous vous demanderons de reconnaître les [conditions de licence](https://visualstudio.microsoft.com/license-terms/) Microsoft et l’énoncé de confidentialité [Microsoft](https://privacy.microsoft.com/privacystatement). Choisissez **Continuer**.

### <a name="step-4---choose-workloads"></a>Étape 4 : Choisir les charges de travail

Une fois l’installateur installé, vous pouvez l’utiliser pour personnaliser votre installation en sélectionnant les charges de travail, ou les ensembles de *fonctionnalités,* que vous voulez. Voici comment faire.

1. Recherchez la charge de travail que vous voulez dans l’écran **Installation de Visual Studio**.

   ![Visual Studio 2019: Installer une charge de travail](../get-started/media/vs-installer-workloads.png)

   Pour obtenir le support CMD de base, choisissez la charge de travail « Développement de bureau avec CMD ». Elle comprend l’éditeur principal par défaut, qui inclut une prise en charge de la modification du code de base pour plus de 20 langues, la possibilité d’ouvrir et de modifier le code dans n’importe quel dossier sans projet et un contrôle de code source intégré.

   Des charges de travail supplémentaires prennent en charge d’autres types de développement de C. Par exemple, choisissez la charge de travail de « développement de la plate-forme Windows universelle » pour créer des applications qui utilisent windows Runtime pour le Microsoft Store. Choisissez « Développement de jeu avec C » pour créer des jeux qui utilisent DirectX, Unreal et Cocos2d. Choisissez le « développement Linux avec C » pour cibler les plates-formes Linux, y compris le développement IoT.

   Le volet **de détails d’installation** répertorie les composants inclus et optionnels installés par chaque charge de travail. Vous pouvez sélectionner ou désélectionner les composants optionnels dans cette liste. Par exemple, pour soutenir le développement en utilisant les ensembles d’outils compilateur Visual Studio 2017 ou 2015, choisissez les composants OPTIONnels MSVC v141 ou MSVC v140. Vous pouvez ajouter un support pour MFC, l’extension de langage expérimentale modules, IncrediBuild, et plus encore.

1. Après avoir choisi la charge de travail et les composants optionnels que vous voulez, choisissez **Install**.

   Ensuite, des écrans d’état affichent la progression de votre installation de Visual Studio.

> [!TIP]
> À tout moment après l’installation, vous pouvez installer les charges de travail ou les composants que vous n’avez pas installés au début. Si vous avez Visual Studio ouvert, allez à **Tools** > **Get Tools and Features ...** qui ouvre l’installateur Studio visuel. Vous pouvez également ouvrir **Visual Studio Installer** à partir du menu Démarrer. À partir de là, vous pouvez choisir les charges de travail ou les composants à installer. Ensuite, choisissez **Modifier**.

### <a name="step-5---choose-individual-components-optional"></a>Étape 5 : Choisir des composants individuels (facultatif)

Si vous ne souhaitez pas utiliser la fonction charge de travail pour personnaliser votre installation Visual Studio, ou si vous souhaitez ajouter plus de composants qu’une charge de travail installe, vous pouvez le faire en installant ou en ajoutant des composants individuels à partir de **l’onglet Composants individuels.** Choisissez ce que vous voulez, puis suivez les invites.

  ![Visual Studio 2019 - Installer des composants individuels](../get-started/media/vs-installer-individual-components.png "Installer des composants individuels Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Étape 6 : Installer les modules linguistiques (facultatif)

Par défaut, le programme d’installation essaie d’installer la langue du système d’exploitation quand vous l’exécutez pour la première fois. Pour installer Visual Studio dans la langue de votre choix, choisissez l’onglet **Modules linguistiques** dans Visual Studio Installer, puis suivez les invites.

  ![Visual Studio 2019 - Installer des packs de langue](../get-started/media/vs-installer-language-packs.png "Installer des packs de langage Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Changer la langue du programme d’installation à partir de la ligne de commande

Une autre façon de changer la langue par défaut consiste à exécuter le programme d’installation à partir de la ligne de commande. Par exemple, vous pouvez forcer le programme d’installation à s’exécuter en anglais en utilisant la commande suivante : `vs_installer.exe --locale en-US`. L’installateur se souviendra de ce paramètre lorsqu’il sera exécuté la prochaine fois. Le programme d’installation prend en charge les jetons de langue suivants : zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru et tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Étape 7 : Changer l’emplacement d’installation (facultatif)

Vous pouvez réduire l’empreinte de l’installation de Visual Studio sur votre lecteur système. Vous pouvez choisir de déplacer le cache de téléchargement, les composants partagés, les SDK et les outils vers d’autres lecteurs et de conserver Visual Studio sur le lecteur qui l’exécute le plus rapidement.

  ![Visual Studio 2019 - Changement d’installation](../get-started/media/vs-installer-installation-locations.png "Modifier l’emplacement de l’installation")

> [!IMPORTANT]
> Vous pouvez sélectionner un autre lecteur uniquement lors de la première installation de Visual Studio. Si vous l’avez déjà installé et que vous souhaitez changer de lecteur, vous devez désinstaller Visual Studio, puis le réinstaller.

### <a name="step-8---start-developing"></a>Étape 8 : Démarrer le développement

1. Une fois l’installation de Visual Studio terminée, choisissez le bouton **Lancer** pour commencer le développement avec Visual Studio.

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

1. Dans la zone de recherche, entrez le type d’application à créer pour voir la liste des modèles disponibles. La liste des modèles varie selon les charges de travail que vous avez choisies lors de l’installation. Pour voir différents modèles, choisissez différentes charges de travail.

   Vous pouvez également filtrer votre recherche sur un langage de programmation spécifique à l’aide de la liste déroulante **Langage**. Vous pouvez aussi filtrer à l’aide de la liste **Plateforme** et de la liste **Type de projet**.

1. Visual Studio ouvre votre nouveau projet. Vous êtes prêt à coder !

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Installation de Visual Studio 2017

Dans Visual Studio 2017, il est facile de choisir et d’installer uniquement les fonctionnalités dont vous avez besoin. Et, en raison de son empreinte minimale réduite, elle s’installe rapidement avec un impact moindre sur le système.

### <a name="prerequisites"></a>Prérequis

- Une connexion Internet à large bande. L’installateur Visual Studio peut télécharger plusieurs gigaoctets de données.

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour une expérience de développement optimale. Assurez-vous que les dernières mises à jour sont appliquées à votre système avant d’installer Visual Studio.

- Assez d’espace disque libre. Visual Studio nécessite au moins 7 Go d’espace disque, et peut prendre 50 Go ou plus si de nombreuses options courantes sont installées. Nous vous recommandons de l’installer sur votre C: lecteur.

Pour plus de détails sur l’espace du disque et les exigences du système d’exploitation, voir [Visual Studio Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-vs). L’installateur indique la quantité d’espace de disque nécessaire pour les options que vous sélectionnez.

### <a name="download-and-install"></a>Télécharger et installer

1. Téléchargez le dernier installateur Visual Studio 2017 pour Windows.

   > [!div class="nextstepaction"]
   > [Installer Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > L’édition Community est destinée aux développeurs individuels, à l’apprentissage en classe, à la recherche académique et au développement open source. Pour les autres utilisations, installez [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ou [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Trouvez le fichier d’installateur que vous avez téléchargé et exécutez-le. Il peut être affiché dans votre navigateur, ou vous pouvez le trouver dans votre dossier Téléchargements. L’installateur a besoin de privilèges d’administrateur pour fonctionner. Vous pouvez voir un dialogue **de contrôle de compte utilisateur** vous demandant de donner la permission de laisser l’installateur apporter des modifications à votre système; choisir **Oui**. Si vous rencontrez des problèmes, trouvez le fichier téléchargé dans File Explorer, cliquez à droite sur l’icône de l’installateur et choisissez **Run en tant qu’administrateur** dans le menu contextuelle.

   ![Télécharger et installer l’installateur Visual Studio](media/vscpp-concierge-run-installer.gif "Télécharger et installer l’installateur Visual Studio")

1. Le programme d’installation vous présente une liste de charges de travail, qui sont des groupes d’options connexes pour des types de développement spécifiques. La prise en charge de CMD fait maintenant partie des charges de travail facultatives qui ne sont pas installées par défaut.

   ![Développement de bureau avec charge de travail de C](media/desktop-development-with-cpp.png "Développement Desktop en C++")

   Pour le C, sélectionnez le développement de bureau avec la charge de travail **de CMD,** puis choisissez **Install**.

   ![Installer le développement de bureau avec la charge de travail de C](media/vscpp-concierge-choose-workload.gif "Installer le développement de bureau avec la charge de travail de C")

1. Lorsque l’installation se termine, choisissez le bouton **Lancement** pour démarrer Visual Studio.

   La première fois que vous exécutez Visual Studio, on vous demande de vous connecter avec un compte Microsoft. Si vous n’en avez pas, vous pouvez en créer une gratuitement. Vous devez également choisir un thème. Ne vous inquiétez pas, vous pouvez le changer plus tard si vous voulez.

   Il peut prendre Visual Studio plusieurs minutes pour se préparer pour l’utilisation la première fois que vous l’exécutez. Voici à quoi il ressemble dans un time-lapse rapide:

   ![Visual Studio 2017 signez](media/vscpp-quickstart-first-run.gif "Visual Studio 2017 signez")

   Visual Studio commence beaucoup plus vite lorsque vous l’exécutez à nouveau.

1. Lorsque Visual Studio s’ouvre, vérifiez si l’icône du drapeau dans la barre de titre est mise en surbrillance :

   ![Indicateur de notification Visual Studio 2017](media/vscpp-first-start-page-flag.png "Indicateur de notification Visual Studio 2017")

   Si elle est mise en surbrillance, sélectionnez-la pour ouvrir la fenêtre **Notifications.** S’il y a des mises à jour disponibles pour Visual Studio, nous vous recommandons de les installer dès maintenant. Une fois l’installation terminée, redémarrez Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Installation de Visual Studio 2015

Pour installer Visual Studio 2015, accédez à [Télécharger d’anciennes versions de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Exécutez le programme d’installation, choisissez **Installation personnalisée**, puis le composant C++. Pour ajouter la prise en charge de CMD à une installation visual studio 2015 existante, cliquez sur le bouton Windows Start et **tapez Add Remove Programs**. Ouvrez le programme à partir de la liste des résultats et trouvez ensuite votre installation Visual Studio 2015 dans la liste des programmes installés. Double-cliquer, puis choisissez **Modifier** et sélectionner les composants Visual CMd à installer.

En règle générale, nous vous recommandons vivement d’utiliser Visual Studio 2017 même si vous avez besoin de compiler votre code en utilisant le compilateur de Visual Studio 2015. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](../porting/use-native-multi-targeting.md).

::: moniker-end

Lorsque Visual Studio est en cours d’exécution, vous êtes prêt à continuer à l’étape suivante.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un projet CMD](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
