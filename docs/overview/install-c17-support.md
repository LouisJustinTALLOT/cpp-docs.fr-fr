---
title: Installer la prise en charge de C11 et C17 dans Visual Studio
description: Installer la prise en charge SDK Windows et CRT pour C11 et C17 dans Visual Studio
ms.date: 09/11/2020
helpviewer_keywords:
- Install preview Windows SDK
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 9310b0dbb4e436245de820622ec9dd0f52292871
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924416"
---
# <a name="install-c11-and-c17-support-in-visual-studio"></a>Installer la prise en charge de C11 et C17 dans Visual Studio

::: moniker range="<=msvc-150"

La prise en charge des normes C11 et C17 nécessite Visual Studio 2019 version 16,8 ou ultérieure. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range="msvc-160"

La prise en charge des normes C11 et C17 est disponible à partir de Visual Studio 2019 version 16,8. La prise en charge requiert la mise à jour du runtime C universel (UCRT) et des dernières mises à jour SDK Windows pour fonctionner correctement avec le préprocesseur conforme ( [`/Zc:preprocessor`](../build/reference/zc-preprocessor.md) ).

Les versions de SDK Windows correspondent aux versions de système d’exploitation Windows. Étant donné qu’il n’y avait pas de version Windows avec ces modifications, vous aurez besoin d’un *SDK Windows Insider Preview* . Il s’agit d’une préversion de la SDK Windows qui correspond aux builds Windows en cours de *vol* , ou testées, par les Windows Insiders. Après avoir installé le kit de développement logiciel (SDK) Windows 10 Insider Preview, les projets Visual Studio configurés pour utiliser la dernière SDK Windows utilisent la version préliminaire d’Insider.

## <a name="prerequisites"></a>Conditions préalables requises

- Visual Studio 2019 version 16,8 Preview 3 ou version ultérieure installée et en cours d’exécution sur votre ordinateur. Dans l’installation, incluez la charge de travail développement Desktop en C++. Vous pouvez télécharger la dernière version d’évaluation à partir de la page [Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/) . Si Visual Studio n’est pas encore installé, consultez Installation de la [prise en charge de C++ dans Visual Studio](../build/vscpp-step-0-installation.md) pour obtenir des instructions d’installation.

## <a name="step-1-sign-in-by-using-an-insider-microsoft-account"></a>Étape 1 : se connecter à l’aide d’un compte Microsoft Insider

Tout le monde peut créer un [compte Microsoft](https://signup.live.com/) gratuit, puis s’abonner au programme Insider. Accédez à la page [programme Windows Insider pour les développeurs](https://insider.windows.com/for-developers) , choisissez **inscrire** et connectez-vous.

Après vous être inscrit, vous avez la possibilité de démarrer la version Insider de Windows. Cette étape n’est pas nécessaire pour télécharger et utiliser le kit de développement logiciel (SDK) Windows 10 Insider. Lorsque vous vous inscrivez à Windows Insider, il n’est pas automatiquement inscrit sur vos machines pour télécharger de nouveaux vols Windows.

Une fois que vous accédez à la page **de bienvenue du programme Windows Insider** , vous n’avez pas besoin de choisir **Flight Now** . Passez à l’étape suivante pour télécharger le kit de développement logiciel (SDK) Windows 10 Insider preview.

## <a name="step-2-download-the-insider-preview-windows-10-sdk"></a>Étape 2 : Téléchargez le kit de développement logiciel (SDK) Windows 10 Insider preview

Vous pouvez installer le SDK Windows Insider Preview à partir de la page de [téléchargements de Windows Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) . Si vous voyez un message indiquant « vous devez être membre du programme Windows Insider », vérifiez que vous êtes connecté. Utilisez le même compte Microsoft que celui utilisé pour le programme Insider. Si vous voyez un message indiquant « nous sommes désolés, la page que vous avez demandée est introuvable », essayez de modifier les paramètres régionaux de l’URL en en *-US* .

La page Insider prétend que l’utilisation d’un système d’exploitation Windows 10 Insider Preview est requise. C’est le cas uniquement pour une partie du contenu inclus dans le SDK Windows. Ce contenu peut dépendre de nouvelles API qui ne sont pas présentes dans les versions antérieures de Windows. Toutefois, les en-têtes Windows et Universal C Runtime peuvent être installés et utilisables sans système d’exploitation Insider.

Choisissez **obtenir le kit de développement logiciel (SDK) Insider Preview – Build 20211** (ou version ultérieure) pour commencer le téléchargement. Les versions ultérieures du SDK Windows fonctionnent également.

## <a name="step-3-install-the-insider-preview-windows-10-sdk"></a>Étape 3 : installer le kit de développement logiciel (SDK) Windows 10 Insider preview

Le SDK Windows Insider Preview est téléchargé sous forme de *`.iso`* fichier. Ouvrez le dossier qui contient le fichier téléchargé dans l’Explorateur de fichiers. Montez le *`.iso`* fichier, puis exécutez *`WinSDKSetup.exe`* pour démarrer l’installation.

Dans la page **spécifier l’emplacement** , sélectionnez **installer le kit de développement logiciel (SDK) Windows- \<version> sur cet ordinateur** , puis choisissez **suivant** . Sur la page **confidentialité des kits Windows** , indiquez si vous souhaitez autoriser Microsoft à collecter des Insights pour les kits Windows 10, puis choisissez **suivant** . Choisissez **accepter** pour accepter le contrat de licence. Dans la page **Sélectionner les fonctionnalités à installer** , sélectionnez uniquement les fonctionnalités suivantes :  

- Outils de signature SDK Windows pour les applications de bureau

- SDK Windows pour les applications gérées UWP

- SDK Windows pour les applications C++ UWP

- SDK Windows pour les applications Desktop C++ x86 (si vous envisagez de générer pour x86)

- SDK Windows pour les applications Desktop C++ amd64 (si vous envisagez de générer pour amd64)

- SDK Windows pour les applications ARM C++ Desktop (si vous envisagez de créer pour ARM)

- SDK Windows pour les applications arm64 C++ Desktop (si vous envisagez de générer pour arm64)

![Capture d’écran du programme d’installation de SDK Windows, montrant les composants sélectionnés pour l’installation](media/c11-7-windows-sdk-installer-select-features.png)

Choisissez **installer** pour installer les composants du kit de développement logiciel (SDK) sélectionnés. Le kit de développement logiciel (SDK) prend quelques minutes pour terminer l’installation. Une fois l’opération terminée, ouvrez Visual Studio.

## <a name="step-4-configuring-c11-or-c17-mode-in-visual-studio"></a>Étape 4 : configuration du mode C11 ou C17 dans Visual Studio

Dans Visual Studio, ouvrez un projet C nouveau ou existant, puis ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

Définissez le projet pour utiliser la version préliminaire du kit de développement logiciel (SDK) Windows 10. Sur la page **Propriétés de configuration**  >  **général** , définissez la propriété **SDK Windows version** sur **10,0 (dernière version installée)** ou sur la version préliminaire spécifique que vous avez installée.

Vous verrez également une nouvelle option : **norme du langage C** . Définissez cette propriété sur **ISO C11 standard ( `/std:c11` )** ou **ISO C17 (2018) standard ( `/std:c17` )** .  

![Capture d’écran de la boîte de dialogue pages de propriétés sur la page Propriétés de configuration général, montrant la sélection de la propriété standard du langage C comme ISO C 17](media/c11-9-project-property-page-c-language-standard.png)

La norme du langage C++ est utilisée lorsque le langage est C++. Il s’agit de la valeur par défaut lorsque l’extension de fichier est *`.cpp`* . La version standard du langage C est utilisée lorsque la langue est C. Il s’agit de la valeur par défaut lorsque l’extension de fichier est *`.c`* . Pour générer en utilisant C11 ou C17, placez votre code source dans un *`.c`* fichier ou définissez le code pour qu’il soit compilé en tant que C. Vous pouvez définir cette propriété pour votre projet dans la page **Propriétés de configuration**  >  **C/C++**  >  **avancé** . Affectez à la propriété **compiler en tant** que la valeur **compiler en code C (/TC)** .

Félicitations, vous avez configuré tout ce dont vous avez besoin pour générer le code C11 et C17 dans Visual Studio 2019 version 16,8 Preview 3 !

## <a name="see-also"></a>Voir aussi

[`/std` (Spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)

::: moniker-end
