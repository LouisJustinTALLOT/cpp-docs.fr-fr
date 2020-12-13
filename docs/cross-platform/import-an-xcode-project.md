---
description: 'En savoir plus sur : importer un projet XCode'
title: Importer un projet Xcode
ms.date: 10/17/2019
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.openlocfilehash: b993e3aa469f93d2bb55604a42ce327e6105ae94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333964"
---
# <a name="import-an-xcode-project"></a>Importer un projet Xcode

Les outils Visual Studio pour le développement mobile multiplateforme avec C++ incluent la prise en charge du déplacement de vos projets Xcode dans Visual Studio, où vous pouvez créer des bibliothèques multiplateformes et partager du code avec d’autres projets. L’Assistant importation à partir de Xcode simplifie le processus d’importation des projets et de fractionnement du code C++ dans vos cibles Xcode pour une utilisation en tant que bibliothèque statique ou projet de code partagé. Vous pouvez gérer votre code spécifique à iOS dans Visual Studio tout en continuant à utiliser Xcode pour effectuer des storyboards et des builds. Pour plus d’informations sur la façon de déplacer facilement du code entre Visual Studio et Xcode, consultez [synchroniser les modifications entre Xcode et Visual Studio](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Utiliser l’Assistant importation à partir de Xcode

Cet article explique comment déplacer un projet XCode vers Visual Studio pour tirer parti du partage de code et des solutions multiplateformes. Comme condition préalable, vous devez associer votre Mac à Visual Studio pour importer, exporter et générer votre projet. Pour obtenir des instructions sur la configuration de l’appariement, consultez [installer et configurer des outils de génération à l’aide d’iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Vous devez également soit partager votre projet XCode sur le réseau, soit le déplacer sur votre ordinateur Visual Studio pour utiliser l’Assistant importation à partir de Xcode.

### <a name="import-from-xcode"></a>Importer à partir de Xcode

1. Dans le menu **fichier** , choisissez **nouveau**, **Importer**, **Importer à partir de Xcode**. Cette commande démarre la boîte de dialogue de l’Assistant **importation à partir de Xcode** .

   ![Choisir le projet de cible Xcode à importer](../cross-platform/media/cppmdd-u2-importxcode-choose.png "Choisir le projet de cible Xcode à importer")

1. Dans le volet **choisir un projet** , choisissez le bouton Parcourir pour sélectionner un fichier Xcode *. pbxproj* . Accédez au fichier projet dans la boîte de dialogue **Sélectionner le fichier de projet XCode** , puis choisissez **ouvrir**.

   ![Sélectionnez un fichier projet dans la boîte de dialogue Sélectionner le fichier projet XCode](../cross-platform/media/cppmdd-u2-importxcode-browse.png "Sélectionnez un fichier projet dans la boîte de dialogue Sélectionner le fichier projet XCode")

   Dans l’Assistant importation à partir de Xcode, choisissez **suivant**.

1. Dans le volet **cibles de destination** , choisissez les cibles du projet XCode à importer dans les projets Visual Studio. Les cibles Xcode sont similaires aux projets Visual Studio. la plupart sont une collection de code et de ressources qui produisent un binaire. L’Assistant importation à partir de Xcode autorise uniquement l’importation de cibles qui produisent un binaire, mais pas une bibliothèque statique, en tant que cibles de destination. Les cibles de bibliothèque statique Xcode font l’objet de l’étape suivante.

   ![Importer à partir de Xcode, Assistant cibles de destination](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "Importer à partir de Xcode, Assistant cibles de destination")

   Pour chaque cible sélectionnée dans **Cibles à importer**, l’Assistant détecte automatiquement les fichiers de code C++ qui peuvent être fractionnés en projet de bibliothèque statique distinct, puis les place dans la section **Éléments de projet C++**. Le reste du code et des ressources se trouve dans la section **éléments de projet XCode** . Une fois que l’Assistant a effectué le processus d’importation, ils deviennent des projets de bibliothèque statique et d’application distincts dans Visual Studio. Par défaut, les cibles de test unitaire et d’infrastructure ne sont pas fractionnées en projets séparés par l’Assistant.

   Pour changer les fichiers contenus dans chaque projet, utilisez les boutons de déplacement vers le haut et le bas. Lorsque vous êtes satisfait des fichiers de chaque projet, choisissez **suivant** pour continuer.

1. Dans le volet **cibles de bibliothèque** , choisissez les cibles de bibliothèque statique du projet XCode à importer dans les projets Visual Studio. Dans ce volet, vous pouvez choisir les fichiers à placer dans un projet de code partagé et les fichiers à placer dans un projet de bibliothèque statique. Dans chacune des cibles de la liste **cibles à importer** , vous pouvez contrôler les fichiers à placer dans les **éléments de projet de code partagé** et les **éléments de projet de bibliothèque statique** à l’aide des boutons monter et descendre.

   ![Importer à partir du volet cibles de la bibliothèque Xcode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "Importer à partir du volet cibles de la bibliothèque Xcode")

   Un projet de code partagé est un moyen de partager un ensemble de fichiers sources entre des projets dans Visual Studio. Le code est généré dans le cadre du projet où il se trouve, et non en tant que projet à part entière. Les projets qui incluent le code partagé peuvent avoir des architectures et des configurations différentes. Un projet de code partagé est la meilleure façon de fournir un projet unique contenant du code qui peut être généré pour de nombreux genres de plateformes.

   Lorsque vous êtes satisfait des fichiers de chaque projet, choisissez **suivant** pour continuer.

1. Utilisez le volet **propriétés globales** pour définir un chemin de recherche de Framework et un chemin de recherche d’en-tête include pour tous les projets iOS dans Visual Studio. Visual Studio utilise ces chemins pour la recherche du code source et pour IntelliSense. Ces chemins globaux sont utiles quand vous créez des projets iOS qui utilisent un ensemble commun d’en-têtes et de frameworks.

   ![Importer à partir du volet Propriétés globales de Xcode](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "Importer à partir du volet Propriétés globales de Xcode")

   Vous pouvez également définir ces chemins globaux dans Visual Studio, dans la boîte de dialogue **Options**. Pour les trouver, dans le menu **Outils**, sélectionnez **Options**. Dans la boîte de dialogue **options** , développez les   >    >    >  **propriétés globales** iOS multiplateforme C++.

   Choisissez **Suivant** pour continuer.

1. Le volet **Frameworks** permet de configurer les chemins utilisés par Visual Studio pour parcourir les éléments de votre projet, ainsi que pour IntelliSense. Les chemins d’accès doivent être accessibles à Visual Studio pour chaque Framework référencé par votre projet XCode. L’Assistant vérifie les références de Framework dans les projets Xcode et indique si Visual Studio peut trouver le Framework. Si vous avez déjà configuré un chemin dans les propriétés globales, il doit être découvert par Visual Studio. Les exceptions sont répertoriées dans la liste Frameworks. Pour chaque framework listé avec un X, indiquez un chemin accessible au PC afin de permettre à Visual Studio de trouver le framework. Vous pouvez utiliser le bouton Parcourir **...** pour utiliser la boîte de dialogue **Sélectionner un dossier** et rechercher le chemin d’accès. Le chemin du framework peut être celui d’une copie locale ou d’un partage réseau sur votre Mac.

   ![Importer à partir du volet frameworks Xcode](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "Importer à partir du volet frameworks Xcode")

   Choisissez **Suivant** pour continuer.

1. Le volet **Paramètres du projet** vous permet de changer le framework et d’inclure les paramètres du chemin de recherche de fichiers d’en-tête Include pour chaque projet créé par l’Assistant. Utilisez ce volet pour définir les chemins spécifiques au projet qui diffèrent des paramètres globaux.

   Pour définir un chemin d’accès pour un projet spécifique, dans la liste déroulante **projet de destination** , sélectionnez le fichier projet. Ensuite, définissez les valeurs dans les contrôles **chemin de recherche** de l’infrastructure et inclure le chemin de **recherche d’en-tête** . Vous pouvez utiliser le bouton Parcourir **...** en regard de chaque contrôle pour utiliser une boîte de dialogue **Sélectionner un dossier** pour rechercher le chemin d’accès.

   ![Importer à partir du volet projets Xcode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "Importer à partir du volet projets Xcode")

   Si aucun Mac distant n’a été associé à ce PC dans Visual Studio, le lien **configurer un ordinateur distant** s’affiche. Pour obtenir des instructions sur la configuration de l’appariement, consultez [installer et configurer des outils de génération à l’aide d’iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Pour importer le projet XCode à l’aide des paramètres de l’Assistant, choisissez **Importer**.

   L’Assistant importation à partir de Xcode crée des projets dans Visual Studio qui correspondent aux cibles de projet XCode sélectionnées. Le code partageable avec d’autres projets C++ est fractionné en projets de code partagé et de bibliothèque statique distincts. Le code restant est placé dans les projets de bibliothèque iOS et d’application qui peuvent être générés à distance par Visual Studio. Pour plus d’informations sur le déplacement de code entre Visual Studio et Xcode, consultez [synchroniser les modifications entre Xcode et Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Installer le développement mobile multiplateforme avec C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
