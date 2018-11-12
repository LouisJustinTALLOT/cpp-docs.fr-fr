---
title: Éditeur de la barre d’outils (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar.F1
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 7efff3d4d784de6ee3130c3481f3674351cc7463
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486054"
---
# <a name="toolbar-editor-c"></a>Éditeur de la barre d’outils (C++)

Le **barre d’outils** éditeur vous permet de créer des ressources de barre d’outils C++ et convertir des bitmaps en ressources de barre d’outils. Le **barre d’outils** éditeur utilise un affichage graphique pour afficher une barre d’outils et les boutons qui ressemblent étroitement à leur aspect dans une application finie.

Avec le **barre d’outils** éditeur, vous pouvez :

- [Créer des boutons et des barres d’outils](../windows/creating-new-toolbars.md)

- [Convertir des bitmaps en ressources de barres d’outils](../windows/converting-bitmaps-to-toolbars.md)

- [Créer, déplacer et modifier des boutons de barres d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [Créer des info-bulles](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

Le **barre d’outils** fenêtre de l’éditeur affiche deux vues d’une image du bouton, identique à la fenêtre d’éditeur d’Image. Une barre de fractionnement sépare les deux volets. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif. Au-dessus des deux affichages de l’image figure la barre d’outils de sujet.

![Barre d’outils Éditeur](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") éditeur de la barre d’outils

Le **barre d’outils** éditeur est similaire à la **Image** éditeur dans la fonctionnalité. Les éléments de menu, outils de graphique et grille de bitmap sont les mêmes que celles figurant dans le **Image** éditeur. Il existe une commande de menu sur le **Image** menu vous permet de basculer entre le **barre d’outils** éditeur et le **Image** éditeur. Pour plus d’informations sur l’utilisation de la **Graphics** barre d’outils, **couleurs** palette, ou **Image** menu, consultez [Éditeur d’images](../windows/image-editor-for-icons.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)