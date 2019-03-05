---
title: Styles du contrôle Progress
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 3adbd32456b1375bd2dc8574220e083ca3d83ee9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296330"
---
# <a name="styles-for-the-progress-control"></a>Styles du contrôle Progress

Lorsque vous créez initialement du contrôle progress ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), utilisez le *dwStyle* paramètre pour spécifier les styles de fenêtre souhaitée pour votre contrôle de progression. La liste suivante décrit en détail les styles de fenêtre applicables. Le contrôle ignore tout style de fenêtre différent de ceux répertoriés ici. Vous devez toujours créer le contrôle comme une fenêtre enfant, généralement d’une boîte de dialogue parent.

|Style de fenêtre|Effet|
|------------------|------------|
|WS_BORDER|Crée une bordure autour de la fenêtre.|
|WS_CHILD|Crée une fenêtre enfant (doit toujours être utilisé pour `CProgressCtrl`).|
|WS_CLIPCHILDREN|Exclut la zone occupée par les fenêtres enfants lorsque vous dessinez dans la fenêtre parente. Utilisé lorsque vous créez la fenêtre parente.|
|WS_CLIPSIBLINGS|Coupe les fenêtres enfants par rapport aux autres.|
|WS_DISABLED|Crée une fenêtre qui est initialement désactivée.|
|WS_VISIBLE|Crée une fenêtre est visible initialement.|
|WS_TABSTOP|Spécifie que le contrôle peut recevoir le focus lorsque l’utilisateur appuie sur la touche TAB pour passer à ce dernier.|

En outre, vous pouvez spécifier deux styles qui s’appliquent uniquement à du contrôle progress, PBS_VERTICAL et PBS_SMOOTH.

Utilisez PBS_VERTICAL pour orienter le contrôle verticalement, et non horizontalement. Utilisez PBS_SMOOTH pour remplir le contrôle complètement, au lieu d’afficher les petits carrés qui remplissent le contrôle de façon incrémentielle.

Sans PBS_SMOOTH (style) :

![Style de barre de progression standard](../mfc/media/vc4ruw1.gif "style de barre de progression Standard")

Avec les styles PBS_SMOOTH et PBS_VERTICAL :

![Style, lisse et vertical de la barre de progression](../mfc/media/vc4ruw2.gif "style, lisse et vertical de la barre de progression")

Pour plus d’informations, consultez [Styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) dans le *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)
