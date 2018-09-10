---
title: Création d’une info-bulle pour un bouton de barre d’outils (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e5fef71d3fa2ad76192a06603ed9e22d52eef71
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317821"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>Création d’une info-bulle pour un bouton de barre d’outils (C++)

### <a name="to-create-a-tool-tip"></a>Pour créer une info-bulle

1. Sélectionnez le bouton de barre d’outils.

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **invite** champ de propriété, ajoutez une description du bouton de la barre d’état ; après le message, ajoutez `\n` et l’info-bulle nom.

Un exemple courant d’une info-bulle est le **impression** situé dans **WordPad**:

1. Ouvrez **WordPad**.

2. Placez le pointeur de la souris sur le **impression** bouton de barre d’outils.

3. Notez que le mot `Print` s’affiche sous le pointeur de la souris.

4. Examinez la barre d’état (tout en bas de la **WordPad** fenêtre)-il affiche le texte `Prints the active document`.

Le `Print` dans **étape 3** est « info-bulle nom » et le `Prints the active document` de **étape 4** est « description du bouton de la barre d’état. »

Si vous souhaitez que cet effet à l’aide de la **barre d’outils** éditeur, vous définissez le **invite** propriété `Prints the active document\nPrint`.

> [!NOTE]
> Vous pouvez modifier le texte d’invite à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)