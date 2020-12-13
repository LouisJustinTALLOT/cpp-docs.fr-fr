---
description: 'En savoir plus sur : Recordset : signets et positions absolues (ODBC)'
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
ms.openlocfilehash: b52ca2e43a89a6cab0e9197d8dbf32c321feca5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186114"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset : signets et positions absolues (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Lorsque vous naviguez dans un Recordset, vous avez souvent besoin d’un moyen de revenir à un enregistrement particulier. Le signet et la position absolue d’un enregistrement fournissent deux méthodes de ce type.

Cette rubrique répond aux questions suivantes :

- [Comment utiliser des signets](#_core_bookmarks_in_mfc_odbc).

- [Comment définir l’enregistrement en cours à l’aide de positions absolues](#_core_absolute_positions_in_mfc_odbc).

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a> Signets dans ODBC MFC

Un signet identifie de façon unique un enregistrement. Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas toujours compter sur la position absolue d’un enregistrement, car les enregistrements peuvent être supprimés du Recordset. La méthode fiable pour assurer le suivi de la position d’un enregistrement consiste à utiliser son signet. La classe `CRecordset` fournit des fonctions membres pour :

- En obtenant le signet de l’enregistrement actif, vous pouvez l’enregistrer dans une variable ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Déplacement rapide vers un enregistrement donné en spécifiant son signet, que vous avez enregistré précédemment dans une variable ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

L’exemple suivant montre comment utiliser ces fonctions membres pour marquer l’enregistrement actif et y revenir ultérieurement :

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Vous n’avez pas besoin d’extraire le type de données sous-jacent de l’objet de [classe CDBVariant](../../mfc/reference/cdbvariant-class.md) . Assignez la valeur avec `GetBookmark` et revenez à ce signet avec `SetBookmark` .

> [!NOTE]
> En fonction de votre pilote ODBC et du type de jeu d’enregistrements, les signets peuvent ne pas être pris en charge. Vous pouvez facilement déterminer si les signets sont pris en charge en appelant [CRecordset :: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). En outre, si les signets sont pris en charge, vous devez choisir explicitement de les implémenter en spécifiant l' `CRecordset::useBookmarks` option dans la fonction membre [CRecordset :: Open](../../mfc/reference/crecordset-class.md#open) . Vous devez également vérifier la persistance des signets après certaines opérations sur les jeux d’enregistrements. Par exemple, si vous avez `Requery` un Recordset, les signets ne sont plus valides. Appelez [CDatabase :: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark` .

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a> Positions absolues dans ODBC MFC

Outre les signets, `CRecordset` la classe vous permet de définir l’enregistrement en cours en spécifiant une position ordinale. C’est ce que l’on appelle le positionnement absolu.

> [!NOTE]
> Le positionnement absolu n’est pas disponible sur les recordsets avant uniquement. Pour plus d’informations sur les recordsets avant uniquement, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Pour déplacer le pointeur d’enregistrement actif à l’aide de la position absolue, appelez [CRecordset :: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Lorsque vous transmettez une valeur à `SetAbsolutePosition` , l’enregistrement correspondant à cette position ordinale devient l’enregistrement actif.

> [!NOTE]
> La position absolue d’un enregistrement est potentiellement non fiable. Si l’utilisateur supprime des enregistrements de l’ensemble d’enregistrements, la position ordinale de toute modification d’enregistrement suivante. Les signets sont la méthode recommandée pour déplacer l’enregistrement en cours. Pour plus d’informations, consultez [signets dans ODBC MFC](#_core_bookmarks_in_mfc_odbc).

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)
