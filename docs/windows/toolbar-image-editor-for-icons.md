---
title: Barre d’outils (Éditeur d’images C++ pour les icônes) | Microsoft Docs
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
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed6639bdf86a54689834c6eda03a3b6ec4dd171d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063846"
---
# <a name="toolbar-c-image-editor-for-icons"></a>Barre d’outils (Éditeur d’images C++ pour les icônes)

Le **Éditeur d’images** barre d’outils contient les outils de dessin, peinture, saisie de texte, effacer et manipulation des vues. Il contient également un sélecteur d’options, avec lequel vous pouvez sélectionner des options pour l’utilisation de chaque outil. Par exemple, vous pouvez choisir à partir de différentes largeurs de pinceau facteurs d’agrandissement et des styles de ligne.

> [!NOTE]
> Tous les outils disponibles sur le **Éditeur d’images** barre d’outils sont également disponibles à partir de la **Image** menu (sous le **outils** commande).

![Barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") barre d’outils Éditeur d’images

Pour utiliser le **Éditeur d’images** barre d’outils et **Option** sélecteur, cliquez sur l’outil ou l’option que vous souhaitez.

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Avec le **Option** sélecteur, vous pouvez spécifier la largeur de ligne, trait de pinceau, etc. L’icône sur le **Option** sélecteur bouton change en fonction de l’outil que vous avez sélectionné.

![Dessin&#45;sélecteur de forme dans la barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") sélecteur d’options de la barre d’outils Éditeur d’images

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Affichage ou masquage de la barre d’outils](displaying-or-hiding-the-toolbar-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)