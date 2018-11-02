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
ms.openlocfilehash: e40a923c755f8b32ca3a6ed1884eb7f7a1d6abfb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529335"
---
# <a name="adding-columns-to-the-control-report-view"></a>Ajout de colonnes au contrôle (vue Rapport)

> [!NOTE]
>  La procédure suivante s’applique à soit un [CListView](../mfc/reference/clistview-class.md) ou [CListCtrl](../mfc/reference/clistctrl-class.md) objet.

Lorsqu’un contrôle de liste est en mode rapport, les colonnes sont affichées, fournissant une méthode d’organiser les différents sous-éléments de chaque élément de contrôle de liste. Cette organisation est implémentée avec une correspondance univoque entre une colonne dans le contrôle de liste et le sous-élément associé de l’élément de contrôle de liste. Pour plus d’informations sur les sous-éléments, consultez [Ajout d’éléments au contrôle](../mfc/adding-items-to-the-control.md). Un exemple d’un contrôle de liste dans la vue rapport est fourni par la vue de détails dans Windows 95 et Windows 98 Explorer. La première colonne répertorie les dossiers, les icônes de fichiers et des étiquettes. Autres colonnes répertorient la taille de fichier, type de fichier, date de dernière modifié et ainsi de suite.

Même si les colonnes peuvent être ajoutées à un contrôle de liste à tout moment, les colonnes sont visibles uniquement lorsque le contrôle a le `LVS_REPORT` bit de style sous tension.

Chaque colonne a un élément d’en-tête associée (consultez [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objet qui étiquette la colonne et permet aux utilisateurs de redimensionner la colonne.

Si votre contrôle de liste prend en charge une vue de rapport, vous devez ajouter une colonne pour chaque sous-élément possible dans un élément de contrôle de liste. Ajouter une colonne en préparant un [structure LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) structure et un appel à [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Après avoir ajouté les colonnes nécessaires (parfois appelées éléments d’en-tête), vous pouvez les réorganiser à l’aide des fonctions membres et des styles appartenant au contrôle header incorporé. Pour plus d’informations, consultez [tri des éléments dans le contrôle Header](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Si le contrôle de liste est créé avec le **LVS_NOCOLUMNHEADER** style, toute tentative pour insérer des colonnes est ignorée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

