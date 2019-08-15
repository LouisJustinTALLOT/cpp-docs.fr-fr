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
ms.openlocfilehash: 9321a582f223269ee998dccd01721f47d90eb7fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509347"
---
# <a name="adding-columns-to-the-control-report-view"></a>Ajout de colonnes au contrôle (vue Rapport)

> [!NOTE]
>  La procédure suivante s’applique à un objet [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md) .

Lorsqu’un contrôle de liste est en mode rapport, les colonnes sont affichées, fournissant ainsi une méthode d’organisation des différents sous-éléments de chaque élément de contrôle de liste. Cette organisation est implémentée avec une correspondance un-à-un entre une colonne dans le contrôle de liste et le sous-élément associé de l’élément de contrôle de liste. Pour plus d’informations sur les sous-éléments, consultez [Ajout d’éléments au contrôle](../mfc/adding-items-to-the-control.md). Un exemple de contrôle de liste en mode rapport est fourni par le mode Détails dans Windows 95 et l’Explorateur Windows 98. La première colonne répertorie les dossiers, les icônes de fichiers et les étiquettes. Les autres colonnes répertorient la taille du fichier, le type de fichier, la date de dernière modification, etc.

Même si les colonnes peuvent être ajoutées à un contrôle de liste à tout moment, elles ne sont visibles que si le bit `LVS_REPORT` de style du contrôle est activé.

Chaque colonne est associée à un élément d’en-tête (voir [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) qui étiquette la colonne et permet aux utilisateurs de redimensionner la colonne.

Si votre contrôle de liste prend en charge une vue rapport, vous devez ajouter une colonne pour chaque sous-élément possible dans un élément de contrôle de liste. Ajoutez une colonne en préparant une structure [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) , puis en effectuant un appel à [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Après avoir ajouté les colonnes nécessaires (parfois appelées éléments d’en-tête), vous pouvez les réorganiser à l’aide de fonctions membres et de styles appartenant au contrôle d’en-tête incorporé. Pour plus d’informations, consultez [classement des éléments dans le contrôle header](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Si le contrôle de liste est créé avec le style **LVS_NOCOLUMNHEADER** , toute tentative d’insertion de colonnes sera ignorée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
