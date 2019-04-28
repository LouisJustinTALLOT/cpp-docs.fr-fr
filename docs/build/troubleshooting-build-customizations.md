---
title: Dépannage des personnalisations de génération
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 7a45b449dc9c3c4c81add37bbac0813c81133203
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315246"
---
# <a name="troubleshooting-build-customizations"></a>Dépannage des personnalisations de génération

Si vos événements ou étapes de build personnalisées ne se comportent pas comme prévu, il existe plusieurs actions à entreprendre pour essayer d’identifier le problème.

- Vérifiez que les fichiers générés par les étapes de build personnalisées correspondent aux fichiers que vous déclarez en tant que sorties.

- Si vos étapes de build personnalisées génèrent des fichiers qui sont des entrées ou des dépendances d’autres étapes de build (personnalisées ou autre), assurez-vous que ces fichiers sont ajoutés à votre projet. Vérifiez également que les outils qui consomment ces fichiers s’exécutent après l’étape de build personnalisée.

- Pour afficher les opérations réelles de l’étape de build personnalisée, ajoutez `@echo on` en tant que première commande. Les événements et les étapes de build sont placés dans un fichier .bat temporaire et exécutés quand le projet est généré. Par conséquent, vous pouvez ajouter la vérification des erreurs à vos commandes d’événement ou d’étape de build.

- Examinez le journal de génération dans le répertoire des fichiers intermédiaires pour voir ce qui a réellement été exécuté. Le chemin et le nom du journal de génération sont représentés par l’expression de macro **MSBuild**, **$(IntDir)\\$(MSBuildProjectName).log**.

- Modifiez les paramètres de votre projet pour collecter davantage que la quantité d’informations par défaut du journal de génération. Dans le menu **Outils**, cliquez sur **Options**. Dans la boîte de dialogue **Options**, cliquez sur le nœud **Projets et solutions**, puis sur le nœud **Générer et exécuter**. Ensuite, dans la zone **Commentaires du fichier journal de génération du projet MSBuild**, cliquez sur **Détaillé**.

- Vérifiez les valeurs des macros de nom de fichier ou de répertoire que vous utilisez. Vous pouvez répercuter des macros individuellement, ou vous pouvez ajouter `copy %0 command.bat` au début de votre étape de build personnalisée, ce qui copie les commandes de votre étape de build personnalisée vers command.bat avec toutes les macros développées.

- Exécutez individuellement les étapes de build personnalisées et les événements de build pour vérifier leur comportement.

## <a name="see-also"></a>Voir aussi

[Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md)
