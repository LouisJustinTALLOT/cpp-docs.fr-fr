---
title: Éléments de rappel et masque de rappel
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 1c46f6edb44e4898c0245209ca837cd0eb716304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624973"
---
# <a name="callback-items-and-the-callback-mask"></a>Éléments de rappel et masque de rappel

Pour chacun de ses éléments, un contrôle List View stocke généralement le texte de l’étiquette, l’index de liste d’images des icônes de l’élément et un jeu d’indicateurs binaires pour l’état de l’élément. Vous pouvez définir des éléments individuels comme éléments de rappel, ce qui est utile si votre application stocke déjà certaines des informations relatives à un élément.

Vous définissez un élément en tant qu’élément de rappel en spécifiant les valeurs appropriées pour les `pszText` `iImage` membres et de la `LVITEM` structure (consultez [CListCtrl :: GetItem](reference/clistctrl-class.md#getitem)). Si l’application gère le texte de l’élément ou du sous-élément, spécifiez la valeur **LPSTR_TEXTCALLBACK** pour le `pszText` membre. Si l’application effectue le suivi de l’icône pour l’élément, spécifiez la valeur de **I_IMAGECALLBACK** pour le `iImage` membre.

En plus de définir des éléments de rappel, vous pouvez également modifier le masque de rappel du contrôle. Ce masque est un jeu d’indicateurs binaires qui spécifient les États de l’élément pour lesquels l’application, plutôt que le contrôle, stocke les données actuelles. Le masque de rappel s’applique à tous les éléments du contrôle, contrairement à la désignation de l’élément de rappel, qui s’applique à un élément spécifique. Par défaut, le masque de rappel est égal à zéro, ce qui signifie que le contrôle effectue le suivi de tous les États des éléments. Pour modifier ce comportement par défaut, initialisez le masque avec n’importe quelle combinaison des valeurs suivantes :

- **LVIS_CUT** L’élément est marqué pour une opération couper-coller.

- **LVIS_DROPHILITED** L’élément est mis en surbrillance en tant que cible de glisser-déplacer.

- **LVIS_FOCUSED** L’élément a le focus.

- **LVIS_SELECTED** L’élément est sélectionné.

- **LVIS_OVERLAYMASK** L’application stocke l’index de liste d’images de l’image de superposition actuelle pour chaque élément.

- **LVIS_STATEIMAGEMASK** L’application stocke l’index de liste d’images de l’image d’État actuelle pour chaque élément.

Pour plus d’informations sur la récupération et la définition de ce masque, consultez [CListCtrl :: GetCallbackMask](reference/clistctrl-class.md#getcallbackmask) et [CListCtrl :: SetCallbackMask](reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
