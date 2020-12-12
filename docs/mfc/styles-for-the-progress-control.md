---
description: En savoir plus sur les styles pour le contrôle Progress
title: Styles du contrôle Progress
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: cd6ce1093f8bd2e3271a386e894d1e8dcd1a4fd7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216494"
---
# <a name="styles-for-the-progress-control"></a>Styles du contrôle Progress

Lorsque vous créez initialement le contrôle Progress ([CProgressCtrl :: Create](../mfc/reference/cprogressctrl-class.md#create)), utilisez le paramètre *dwStyle* pour spécifier les styles de fenêtre souhaités pour votre contrôle Progress. La liste suivante détaille les styles de fenêtre applicables. Le contrôle ignore tous les styles de fenêtre autres que ceux répertoriés ici. Vous devez toujours créer le contrôle en tant que fenêtre enfant, généralement un parent de la boîte de dialogue.

|Style de fenêtre|Résultat|
|------------------|------------|
|WS_BORDER|Crée une bordure autour de la fenêtre.|
|WS_CHILD|Crée une fenêtre enfant (doit toujours être utilisée pour `CProgressCtrl` ).|
|WS_CLIPCHILDREN|Exclut la zone occupée par les fenêtres enfants lorsque vous dessinez dans la fenêtre parente. Utilisé lors de la création de la fenêtre parente.|
|WS_CLIPSIBLINGS|Découpe les fenêtres enfants les unes par rapport aux autres.|
|WS_DISABLED|Crée une fenêtre qui est initialement désactivée.|
|WS_VISIBLE|Crée une fenêtre qui est initialement visible.|
|WS_TABSTOP|Spécifie que le contrôle peut recevoir le focus lorsque l’utilisateur appuie sur la touche TAB pour y accéder.|

En outre, vous pouvez spécifier deux styles qui s’appliquent uniquement au contrôle Progress, PBS_VERTICAL et PBS_SMOOTH.

Utilisez PBS_VERTICAL pour orienter le contrôle verticalement, plutôt que horizontalement. Utilisez PBS_SMOOTH pour remplir complètement le contrôle, au lieu d’afficher des petits carrés délimités qui remplissent le contrôle de façon incrémentielle.

Sans PBS_SMOOTH style :

![Style de la barre de progression standard](../mfc/media/vc4ruw1.gif "Style de la barre de progression standard")

Avec les styles PBS_SMOOTH et PBS_VERTICAL :

![Style de la barre de progression, lisse et vertical](../mfc/media/vc4ruw2.gif "Style de la barre de progression, lisse et vertical")

Pour plus d’informations, consultez [styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) dans la *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)
