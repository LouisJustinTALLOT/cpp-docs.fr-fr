---
title: Installer le développement mobile multiplateforme avec C++
ms.date: 10/17/2019
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
ms.openlocfilehash: 6a573b0f7ba261b97af9de24e67f733acac0532f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041950"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installer le développement mobile multiplateforme avec C++

Vous pouvez utiliser C++ dans Visual Studio pour créer des applications de bureau Windows, des applications de plateforme Windows universelle (UWP) et des applications Linux. Et maintenant, vous pouvez générer des applications C++ pour Android et iOS. La charge de travail **développement mobile en C++** est un ensemble de composants installables dans Visual Studio. Il comprend des modèles Visual Studio iOS, Android et UWP multiplateforme. La charge de travail installe les outils multiplateformes et les kits de développement logiciel (SDK) dont vous avez besoin pour commencer rapidement. Vous n’avez pas à les localiser, à les télécharger et à les configurer vous-même. Vous pouvez utiliser ces outils dans Visual Studio pour créer, modifier, déboguer et tester facilement vos projets multiplateformes.

Cet article explique comment installer les outils et les logiciels tiers requis pour développer des applications multiplateformes en C++ à l’aide de Visual Studio. Pour une vue d’ensemble, consultez [Visual C++ multiplateforme mobile](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>Configuration requise

::: moniker range="vs-2017"

- Pour connaître la configuration requise pour l’installation, consultez [Configuration système requise pour la famille de produits Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Si vous utilisez Windows 7 ou Windows Server 2008 R2, vous pouvez développer du code pour les applications de bureau Windows, les bibliothèques et les applications Android Native Activity, ainsi que les applications et les bibliothèques de code pour iOS, mais pas pour les applications Windows Store ou UWP.

::: moniker-end
::: moniker range=">=vs-2019"

- Pour connaître la configuration requise pour l’installation, consultez [Configuration système requise pour la famille de produits Visual Studio](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Si vous utilisez Windows 7 ou Windows Server 2008 R2, vous pouvez développer du code pour les applications de bureau Windows, pour les applications et les bibliothèques Android Native Activity, et pour les applications et les bibliothèques de code pour iOS, mais pas pour les applications Windows Phone ni UWP.

::: moniker-end

Pour créer des applications pour des plateformes d’appareils spécifiques, il y a quelques spécifications requises supplémentaires :

- Les émulateurs Android x86 fournis avec le Android SDK fonctionnent mieux sur les ordinateurs qui peuvent utiliser l’accélération matérielle, tels que le Hardware Accelerated Execution Manager Intel (HAXM). Pour plus d’informations, consultez [accélération matérielle pour les performances de l’émulateur (Hyper-V & HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- La génération de code pour iOS nécessite un ID Apple, un compte iOS Developer Program et un ordinateur Mac pouvant exécuter [Xcode](https://developer.apple.com/xcode/) version 10,2 ou ultérieure sur OS X Mavericks (version 10,9) ou versions ultérieures. Pour obtenir un lien pointant vers la procédure d’installation, consultez [Installer les outils pour iOS](#install-tools-for-ios).

- Les émulateurs Windows Phone nécessitent un ordinateur qui peut exécuter Hyper-V. La fonctionnalité Hyper-V de Windows doit être activée pour permettre l’installation et l’exécution des émulateurs. Pour plus d’informations, consultez la [configuration requise](/visualstudio/cross-platform/system-requirements-for-the-visual-studio-emulator-for-android) de l’émulateur.

## <a name="get-the-tools"></a>Obtenir les outils

Le développement mobile en C++ est disponible dans les éditions Community, Professional et Enterprise de Visual Studio. Pour accéder à Visual Studio, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) . Les outils multiplateformes de développement mobile sont disponibles à partir de Visual Studio 2015.

## <a name="install-the-tools"></a>Installer les outils

Le Visual Studio Installer comprend un **développement mobile avec** une charge de travail C++. Cette charge de travail installe les outils, modèles et composants du langage C++ requis pour le développement Android et iOS dans Visual Studio. Il comprend les ensembles d’outils GCC et Clang nécessaires pour les builds et le débogage Android. La charge de travail installe les composants Android SDK et pour communiquer avec un Mac pour le développement iOS. Il installe également les outils tiers et les kits de développement logiciel requis pour prendre en charge le développement d’applications iOS et Android. La plupart de ces outils tiers sont des logiciels open source nécessaires pour la prise en charge de la plateforme Android.

- Android (Native Development Kit), Apache Ant et les outils de développement C++ Android sont requis pour générer du code C++ qui cible la plateforme Android.

  > [!NOTE]
  > Certains outils de l’Android NDK ne prennent pas en charge les caractères Unicode dans les chemins d’accès et les noms de fichiers. Si un fichier projet ou source contient des caractères Unicode dans son chemin d’accès ou son nom de fichier, la génération du projet échoue.

- Les composants Google Émulateur Android et Intel Hardware Accelerated Execution Manager (HAXM) sont facultatifs, mais recommandés. (Les pilotes Intel HAXM fonctionnent uniquement sur les processeurs Intel et sont incompatibles avec certaines machines virtuelles, y compris Hyper-V.) Vous pouvez développer et déboguer directement sur un appareil Android, mais il est souvent plus facile d’utiliser un émulateur sur votre bureau pour le débogage.

- Les outils de développement iOS c++ sont requis pour générer du code C++ qui cible la plateforme iOS.

> [!NOTE]
> Si vous utilisez Visual Studio 2015, consultez [Installer Visual C++ pour le développement mobile multiplateforme (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015&preserve-view=true)

### <a name="install-the-mobile-development-with-c-workload"></a>Installer la charge de travail Développement mobile en C++

1. Exécutez le **programme d’installation de Visual Studio** à partir du menu **Démarrer**.

1. Si vous avez déjà installé Visual Studio, choisissez le bouton **Modifier** pour la version installée de Visual Studio que vous souhaitez modifier. Sinon, choisissez **Installer** pour installer Visual Studio.

1. Après avoir sélectionné l’onglet **Charges de travail**, faites défiler vers le bas et sélectionnez la charge de travail **Développement mobile en C++** dans le programme d’installation de Visual Studio. Lorsque cette charge de travail est sélectionnée, les autres composants requis pour le développement C++ sont également sélectionnés. Vous pouvez également choisir d’autres charges de travail et composants individuels à installer en même temps. Pour générer un code multiplateforme qui cible la plateforme Windows universelle, sélectionnez la charge de travail **Développement de la plateforme universelle Windows**.

1. Dans le volet **Détails de l’installation**, développez **Développement mobile en C++**. Dans la section **Facultatif**, vous pouvez choisir des versions supplémentaires du NDK, l’émulateur Google Android, Hardware Accelerated Execution Manager et l’outil d’accélération de build IncrediBuild.

1. Par défaut, un ou plusieurs composants du programme d’installation du SDK Android sont inclus par la charge de travail. D’autres versions du SDK Android sont disponibles. Pour en ajouter une à votre installation, choisissez l’onglet **Composants individuels**, puis faites défiler jusqu'à la section **SDK, bibliothèques et frameworks** pour effectuer votre sélection.

1. Choisissez le bouton **Modifier** ou **Installer** pour installer la charge de travail **Développement mobile en C++** et vos autres charges de travail et composants facultatifs sélectionnés.

   À la fin de l’installation, fermez le programme d’installation, puis redémarrez l’ordinateur. Certaines actions d’installation des composants tiers ne prennent effet qu’après le redémarrage de l’ordinateur.

   > [!IMPORTANT]
   > Vous devez redémarrer pour vous assurer que tout est installé correctement.

1. Ouvrez Visual Studio.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Vous pouvez utiliser Visual Studio pour modifier, déboguer et déployer du code iOS sur le simulateur iOS. Ou, sur un appareil iOS. En raison des restrictions de licences, le code doit être généré à distance sur un Mac. Pour générer et exécuter des applications iOS à l’aide de Visual Studio, vous devez d’abord installer et configurer l’agent distant sur votre Mac. Pour obtenir des instructions d’installation détaillées, connaître les prérequis et les options de configuration, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Si vous ne générez pas pour iOS, vous pouvez ignorer cette étape.

## <a name="install-or-update-dependencies-manually"></a>Installer ou mettre à jour manuellement les dépendances

Vous n’êtes pas obligé d’installer toutes les dépendances tierces lorsque vous installez le **développement mobile avec** la charge de travail C++ (ou dans Visual Studio 2015, l’option de développement Visual C++ mobile). Installez-les ultérieurement à l’aide de la procédure décrite dans [installer les outils](#install-the-tools). Le programme d’installation de Visual Studio est régulièrement mis à jour pour installer les derniers composants tiers. Utilisez-le pour installer les kits de développement logiciel (SDK) mis à jour et NDK. Vous pouvez également les installer ou les mettre à jour indépendamment de Visual Studio.

Vous pouvez réexécuter l’application du gestionnaire du SDK dans le répertoire Android SDK pour mettre à jour le kit de développement logiciel (SDK). Et, pour installer des outils facultatifs et des niveaux d’API supplémentaires. L’installation des mises à jour risque d’échouer, sauf si vous utilisez **Exécuter en tant qu’administrateur** pour exécuter l’application du Gestionnaire du SDK. Si vous rencontrez des problèmes lors de la génération d’une application Android, recherchez des mises à jour pour les Kits de développement logiciel installés dans le Gestionnaire du SDK.

Pour utiliser certains des émulateurs Android SDK, vous devrez peut-être configurer l’accélération matérielle. Pour plus d’informations, consultez [accélération matérielle pour les performances de l’émulateur (Hyper-V & HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

Dans la plupart des cas, Visual Studio peut détecter les configurations pour les logiciels tiers que vous avez installés. Il gère les chemins d’installation dans les variables d’environnement internes. Vous pouvez remplacer les chemins par défaut de ces outils de développement multiplateformes dans l’IDE de Visual Studio.

### <a name="to-set-the-paths-for-third-party-tools"></a>Pour définir les chemins des outils tiers

1. Dans la barre de menus de Visual Studio, sélectionnez **Outils**  >  **options**.

1. Dans la boîte de dialogue **Options**, sélectionnez **Multiplateforme** > **C++** > **Android**.

   ![Options de chemin d'accès de l'outil Android](../cross-platform/media/cppmdd-options-android.png "Options de chemin d'accès de l'outil Android")

1. Pour modifier le chemin utilisé par un outil, cochez la case en regard du chemin et modifiez le chemin du dossier dans la zone de texte. Vous pouvez également utiliser le bouton Parcourir (**...**) pour ouvrir une boîte de dialogue **Sélectionner un emplacement** et choisir le dossier.

1. Choisissez **OK** pour enregistrer les emplacements des dossiers d’outils personnalisés.

## <a name="see-also"></a>Voir aussi

[Installer et configurer des outils de génération à l’aide d’iOS](install-and-configure-tools-to-build-using-ios.md)\
[Développement multiplateforme en Visual C++ pour appareils mobiles](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
