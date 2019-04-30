---
title: 'Recordset : Signets et Positions absolues (ODBC)'
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
ms.openlocfilehash: c4a223f01b25b4c321ccfb4f4c03c3c5241381ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395610"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset : Signets et Positions absolues (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Lors de la navigation dans un jeu d’enregistrements, vous avez souvent besoin de revenir à un enregistrement particulier. Signet et la position absolue d’un enregistrement fournissent deux de ces méthodes.

Cette rubrique explique :

- [Comment utiliser des signets](#_core_bookmarks_in_mfc_odbc).

- [Comment définir l’enregistrement en cours à l’aide des positions absolues](#_core_absolute_positions_in_mfc_odbc).

##  <a name="_core_bookmarks_in_mfc_odbc"></a> Signets dans ODBC MFC

Un signet identifie de façon unique un enregistrement. Lorsque vous naviguez dans un jeu d’enregistrements, vous ne pouvez pas compter toujours à la position absolue d’un enregistrement, car les enregistrements peuvent être supprimés du jeu d’enregistrements. La méthode fiable pour suivre la position d’un enregistrement consiste à utiliser un signet. Classe `CRecordset` fournit les fonctions membres pour :

- Obtenir le signet de l’enregistrement en cours, donc vous pouvez l’enregistrer dans une variable ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Atteindre rapidement un enregistrement donné en spécifiant son signet, vous avez enregistré précédemment dans une variable ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

L’exemple suivant illustre l’utilisation de ces fonctions membres pour marquer l’enregistrement en cours et d’y revenir plus tard :

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Vous n’avez pas besoin extraire le type de données sous-jacent à partir de la [CDBVariant (classe)](../../mfc/reference/cdbvariant-class.md) objet. Affectez la valeur avec `GetBookmark` et revenir au signet avec `SetBookmark`.

> [!NOTE]
>  En fonction de votre pilote ODBC et le type de jeu d’enregistrements, les signets ne peuvent pas en charge. Vous pouvez facilement déterminer si les signets sont pris en charge en appelant [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). En outre, si les signets sont pris en charge, vous devez choisir explicitement de les implémenter en spécifiant le `CRecordset::useBookmarks` option dans le [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) fonction membre. Vous devez également vérifier les signets persistent après certaines opérations de jeu d’enregistrements. Par exemple, si vous `Requery` un jeu d’enregistrements, signets peuvent ne plus être valides. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark`.

##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Positions absolues dans ODBC MFC

Outre les signets, classe `CRecordset` vous permet de définir l’enregistrement actif en spécifiant une position ordinale. Il s’agit de positionnement absolu.

> [!NOTE]
>  Le positionnement absolu n’est pas disponible sur les recordsets avant uniquement. Pour plus d’informations à propos des recordsets avant uniquement, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Pour déplacer le pointeur d’enregistrement actuel à l’aide de la position absolue, appelez [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Lorsque vous passez une valeur à `SetAbsolutePosition`, l’enregistrement correspondant à cette position ordinale devienne l’enregistrement actif.

> [!NOTE]
>  La position absolue d’un enregistrement est potentiellement non fiable. Si l’utilisateur supprime des enregistrements du jeu d’enregistrements, la position ordinale d’enregistrements change. Les signets sont la méthode recommandée pour déplacer l’enregistrement actif. Pour plus d’informations, consultez [signets dans ODBC MFC](#_core_bookmarks_in_mfc_odbc).

Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez [jeu d’enregistrements : Défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)