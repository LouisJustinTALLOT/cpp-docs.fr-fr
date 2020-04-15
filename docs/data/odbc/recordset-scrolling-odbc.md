---
title: 'Recordset : défilement (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366938"
---
# <a name="recordset-scrolling-odbc"></a>Recordset : défilement (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Après avoir ouvert un enregistrement, vous devez accéder aux enregistrements pour afficher les valeurs, faire des calculs, générer des rapports, etc. Le défilement vous permet de passer d’un enregistrement à l’autre dans votre dossier.

Cette rubrique répond aux questions suivantes :

- [Comment faire défiler d’un enregistrement à l’autre dans un recordet](#_core_scrolling_from_one_record_to_another).

- [Dans quelles circonstances le défilement est et n’est pas pris en charge](#_core_when_scrolling_is_supported).

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Faire défiler d’un enregistrement à l’autre

La `CRecordset` classe `Move` fournit les fonctions de membre pour le défilement dans un enregistrement. Ces fonctions déplacent l’enregistrement actuel par des rames. Si vous avez mis en `Move` œuvre la rame en vrac, une opération repositionne le recordet de la taille de la ligne. Si vous n’avez pas implémenté `Move` la rame en vrac, un appel à une fonction repositionne le nombre d’enregistrements par un enregistrement à chaque fois. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Lorsque vous passez par un dossier, les enregistrements supprimés peuvent ne pas être ignorés. Pour plus d’informations, consultez la fonction membre [IsDeleted.](../../mfc/reference/crecordset-class.md#isdeleted)

En plus `Move` des fonctions, `CRecordset` fournit des fonctions de membre pour vérifier si vous avez fait défiler au-delà de la fin ou avant le début de votre dossier.

Pour déterminer si le défilement est `CanScroll` possible dans votre dossier, appelez la fonction membre.

#### <a name="to-scroll"></a>Faire défiler

1. En avant d’un enregistrement ou d’un jeu de ligne : appelez la fonction membre [MoveNext.](../../mfc/reference/crecordset-class.md#movenext)

1. Vers l’arrière d’un enregistrement ou d’un jeu de ligne : appelez la fonction membre [MovePrev.](../../mfc/reference/crecordset-class.md#moveprev)

1. Au premier enregistrement de l’enregistrement : appelez la fonction membre [MoveFirst.](../../mfc/reference/crecordset-class.md#movefirst)

1. Au dernier enregistrement dans le jeu d’enregistrement ou au dernier jeu de ligne : appelez la fonction membre [MoveLast.](../../mfc/reference/crecordset-class.md#movelast)

1. *N* enregistrements par rapport à la position actuelle: appelez la fonction membre [Move.](../../mfc/reference/crecordset-class.md#move)

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Pour tester la fin ou le début du recordet

1. Avez-vous fait défiler au-delà du dernier album? Appelez la fonction membre [IsEOF.](../../mfc/reference/crecordset-class.md#iseof)

1. Avez-vous fait défiler en avant du premier album (en reculant)? Appelez la fonction membre [d’IsBOF.](../../mfc/reference/crecordset-class.md#isbof)

L’exemple de `IsBOF` `IsEOF` code suivant utilise et détecte les limites d’un enregistrement lors du défilement dans les deux sens.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF`retourne une valeur non zéro si le recordet est positionné au-delà du dernier enregistrement. `IsBOF`retourne une valeur non zéro si le recordet est placé en avance sur le premier enregistrement (avant tous les enregistrements). Dans les deux cas, il n’y a pas de dossier actuel à utiliser. Si vous `MovePrev` `IsBOF` appelez quand est `MoveNext` `IsEOF` déjà VRAI ou appelez quand `CDBException`est déjà VRAI, le cadre jette un . Vous pouvez `IsBOF` également `IsEOF` utiliser et vérifier un jeu d’enregistrement vide.

Pour plus d’informations sur la navigation de recordset, voir [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Lorsque le défilement est pris en charge

Tel qu’initialement conçu, SQL n’a fourni que le défilement vers l’avant, mais ODBC étend les capacités de défilement. Le niveau de support disponible pour le défilement dépend des pilotes ODBC avec qui votre application travaille, du niveau de conformation ODBC API de votre pilote et de la question de savoir si la bibliothèque de curseurs ODBC est chargée dans la mémoire. Pour plus d’informations, voir [ODBC](../../data/odbc/odbc-basics.md) et [ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
> Vous pouvez contrôler si la bibliothèque de curseurs est utilisée. Voir les paramètres *bUseCursorLib* et *dwOptions* à [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> Contrairement aux classes MFC DAO, les classes MFC ODBC ne fournissent pas un ensemble de `Find` fonctions pour localiser le prochain (ou précédent) enregistrement qui répond à des critères spécifiés.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Recordset : filtrage d'enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
