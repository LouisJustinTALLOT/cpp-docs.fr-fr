---
title: Ajout de colonnes au contrôle (vue Rapport)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 34d7b62985748b9b9d741c083ec9b34fce06b309
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370873"
---
# <a name="adding-columns-to-the-control-report-view"></a>Ajout de colonnes au contrôle (vue Rapport)

> [!NOTE]
> La procédure suivante s’applique à un objet [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl.](../mfc/reference/clistctrl-class.md)

Lorsqu’un contrôle de liste est affiché, des colonnes sont affichées, fournissant une méthode d’organisation des différents sous-éléments de chaque élément de contrôle de liste. Cette organisation est mise en œuvre avec une correspondance individuelle entre une colonne dans le contrôle de liste et le subitem associé de l’élément de contrôle de liste. Pour plus d’informations sur les subitems, voir [Ajouter des éléments au contrôle](../mfc/adding-items-to-the-control.md). Un exemple de contrôle de liste dans la vue de rapport est fourni par la vue Détails dans Windows 95 et Windows 98 Explorer. La première colonne répertorie le dossier, les icônes de fichier et les étiquettes. D’autres colonnes énumèrent la taille du fichier, le type de fichier, la date modifiée pour la dernière fois, et ainsi de suite.

Même si les colonnes peuvent être ajoutées à un contrôle de `LVS_REPORT` liste à tout moment, les colonnes ne sont visibles que lorsque le contrôle a le bit de style allumé.

Chaque colonne dispose d’un objet d’en-tête associé (voir [CHeaderCtrl)](../mfc/reference/cheaderctrl-class.md)qui étiquette la colonne et permet aux utilisateurs de resize la colonne.

Si votre contrôle de liste prend en charge une vue de rapport, vous devez ajouter une colonne pour chaque subitem possible dans un élément de contrôle de liste. Ajoutez une colonne en préparant une structure [LVCOLUMN,](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) puis en faisant un appel à [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Après avoir ajouté les colonnes nécessaires (parfois appelées éléments d’en-tête), vous pouvez les réorganiser en utilisant les fonctions des membres et les styles appartenant au contrôle de l’en-tête intégré. Pour plus d’informations, voir [Commander des éléments dans le contrôle de l’en-tête](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
> Si le contrôle de liste est créé avec le style **LVS_NOCOLUMNHEADER,** toute tentative d’insertion de colonnes sera ignorée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
