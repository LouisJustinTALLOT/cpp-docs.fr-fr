---
title: Volets de fenêtre (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02cc8fed4056199787c3108d287945bb8a0ae7dd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594104"
---
# <a name="window-panes-image-editor-for-icons"></a>Volets de fenêtre (Éditeur d'images pour les icônes)

Le **Éditeur d’images** fenêtre affiche une image en général deux volets séparés par une barre de fractionnement. Une vue est la taille réelle et l’autre est agrandie (facteur d’agrandissement de la valeur par défaut est 6). Les vues dans ces deux volets sont mis à jour automatiquement : les modifications apportées dans un volet sont immédiatement répercutées dans l’autre. Les deux volets facilitent vous permettent de travailler sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer les pixels et, en même temps, observer l’effet de votre travail sur la vue de la taille réelle de l’image.

Le volet gauche utilise autant d’espace nécessaire (la moitié de la **Image** fenêtre) pour afficher la vue 1:1 facteur d’agrandissement (il s’agit de la valeur par défaut) de votre image. Le volet droit affiche l’image agrandie (facteur d’agrandissement 6:1 par défaut). Vous pouvez [modifier le grossissement](../windows/changing-the-magnification-factor-image-editor-for-icons.md) dans chaque volet en utilisant le **Magnify** outil sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou en utilisant les touches accélérateur.

Vous pouvez agrandir le volet de plus petites de la **Éditeur d’images** fenêtre et utiliser les deux volets pour afficher différentes zones d’une grande image. Cliquez sur dans le volet pour le sélectionner.

Vous pouvez modifier les tailles relatives des volets en plaçant le pointeur sur la barre de fractionnement et de déplacement de la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut déplacer jusqu’au côté, si vous souhaitez travailler sur un seul volet.

Si le **Éditeur d’images** est agrandie par un facteur de 4 ou version ultérieure, vous pouvez [afficher une grille de pixels](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) qui délimite les pixels individuels dans l’image.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)  
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)