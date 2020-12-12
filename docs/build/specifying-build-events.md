---
description: 'En savoir plus sur : spécification d’événements de build'
title: Spécification d'événements de build
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: 1d1dc9a1f0e379c3abe36117beaf9ef58bcbd064
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275397"
---
# <a name="specifying-build-events"></a>Spécification d’événements de build

Vous pouvez utiliser des événements de build pour spécifier des commandes qui s’exécutent avant le début de la génération, avant le processus d’édition des liens ou après la génération.

Les événements de build sont exécutés uniquement si la build atteint ces étapes du processus de génération. Si une erreur survient pendant la génération, l’événement *post-build* ne se produit pas ; si l’erreur se produit avant la phase de liaison, ni l’événement *avant l’édition des liens* ni l’événement *post-build* ne se produisent. De plus, si aucun fichier ne doit être lié, l’événement *avant l’édition des liens* ne se produit pas. L’événement *avant l’édition des liens* n’est pas non plus disponible dans les projets qui ne contiennent pas d’étape de liaison.

Si aucun fichier ne doit être généré, aucun événement de build ne se produit.

Pour obtenir des informations générales sur les événements de build, consultez [Présentation des étapes de build personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Pour spécifier un événement de build

1. Dans l’**Explorateur de solutions**, sélectionnez le projet pour lequel vous voulez spécifier l’événement de build.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md).

1. Dans le dossier **Événements de build**, sélectionnez une page de propriétés d’événement de build.

1. Spécifiez les propriétés associées à l’événement de build :

   - Dans **Ligne de commande**, spécifiez une commande comme vous le feriez à une invite de commandes. Spécifiez une commande ou un fichier de commandes valide, ainsi que les fichiers d’entrée ou de sortie requis. Spécifiez la commande batch **call** avant le nom d’un fichier de commandes pour garantir l’exécution de toutes les commandes suivantes.

      Il est possible de spécifier plusieurs fichiers d’entrée et de sortie symboliquement à l’aide de macros MSBuild. Pour plus d’informations sur la façon de spécifier l’emplacement des fichiers, ou les noms des ensembles de fichiers, consultez [macros courantes pour les commandes et les propriétés de génération](reference/common-macros-for-build-commands-and-properties.md).

      Étant donné que le caractère'% 'est réservé par MSBuild, si vous spécifiez une variable d’environnement, remplacez chaque **%** caractère d’échappement par la séquence d’échappement hexadécimale **%25** . Par exemple, remplacez **%WINDIR%** par **%25WINDIR%25**. MSBuild remplace chaque séquence **%25** par le caractère **%** avant d’accéder à la variable d’environnement.

   - Dans **Description**, tapez une description pour cet événement. La description s’affiche dans la fenêtre **Sortie** quand cet événement se produit.

   - Dans **Exclu de la génération**, spécifiez **Oui** si vous ne voulez pas que l’événement soit exécuté.

## <a name="see-also"></a>Voir aussi

[Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md)<br>
[Macros courantes pour les propriétés et les commandes de build](reference/common-macros-for-build-commands-and-properties.md)<br>
[Dépannage des personnalisations de génération](troubleshooting-build-customizations.md)
