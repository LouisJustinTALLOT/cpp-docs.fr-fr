---
title: 'Recordset : signets et positions absolues (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367068"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset : signets et positions absolues (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Lorsque vous naviguez à travers un historique, vous avez souvent besoin d’un moyen de revenir à un dossier particulier. Le signet d’un enregistrement et sa position absolue fournissent deux méthodes de ce type.

Cette rubrique répond aux questions suivantes :

- [Comment utiliser des signets](#_core_bookmarks_in_mfc_odbc).

- [Comment établir le record actuel en utilisant des positions absolues](#_core_absolute_positions_in_mfc_odbc).

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Signets dans MFC ODBC

Un signet identifie de façon unique un enregistrement. Lorsque vous naviguez à travers un historique, vous ne pouvez pas toujours compter sur la position absolue d’un enregistrement parce que les enregistrements peuvent être supprimés de l’enregistrement. La façon fiable de garder une trace de la position d’un enregistrement est d’utiliser son signet. La `CRecordset` classe fournit des fonctions de membre pour :

- Obtenir le signet de l’enregistrement actuel, de sorte que vous pouvez l’enregistrer dans une variable ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Passer rapidement à un enregistrement donné en spécifiant son signet, que vous avez enregistré plus tôt dans une variable ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

L’exemple suivant illustre comment utiliser ces fonctions de membre pour marquer l’enregistrement actuel et y revenir plus tard :

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Vous n’avez pas besoin d’extraire le type de données sous-jacent de l’objet [CDBVariant Class.](../../mfc/reference/cdbvariant-class.md) Attribuer la `GetBookmark` valeur avec et revenir `SetBookmark`à ce signet avec .

> [!NOTE]
> Selon votre pilote ODBC et le type de recordet, les signets peuvent ne pas être pris en charge. Vous pouvez facilement déterminer si les signets sont pris en charge en appelant [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). En outre, si les signets sont pris en charge, `CRecordset::useBookmarks` vous devez explicitement choisir de les implémenter en spécifiant l’option dans la fonction [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) membre. Vous devez également vérifier la persistance des signets après certaines opérations de recordset. Par exemple, `Requery` si vous êtes un carnet, les signets peuvent ne plus être valides. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si `SetBookmark`vous pouvez appeler en toute sécurité .

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Positions absolues dans MFC ODBC

Outre les signets, la classe `CRecordset` vous permet d’établir le record actuel en spécifiant une position ordinaire. C’est ce qu’on appelle le positionnement absolu.

> [!NOTE]
> Le positionnement absolu n’est pas disponible sur les enregistrements avant-seulement. Pour plus d’informations sur les enregistrements avant seuls, voir [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Pour déplacer le pointeur de record actuel en utilisant la position absolue, appelez [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Lorsque vous passez une `SetAbsolutePosition`valeur à , l’enregistrement correspondant à cette position ordinaire devient l’enregistrement actuel.

> [!NOTE]
> La position absolue d’un dossier est potentiellement peu fiable. Si l’utilisateur supprime les enregistrements de l’enregistrement, la position ordinaire de tout changement d’enregistrement ultérieur. Les signets sont la méthode recommandée pour déplacer l’enregistrement actuel. Pour plus d’informations, voir [Signets dans MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Pour plus d’informations sur la navigation de recordset, voir [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)
