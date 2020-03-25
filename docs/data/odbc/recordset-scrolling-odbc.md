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
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212769"
---
# <a name="recordset-scrolling-odbc"></a>Recordset : défilement (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Après avoir ouvert un jeu d’enregistrements, vous devez accéder aux enregistrements pour afficher des valeurs, effectuer des calculs, générer des rapports, etc. Le défilement vous permet de passer d’un enregistrement à un autre dans votre Recordset.

Cette rubrique explique :

- [Comment faire défiler d’un enregistrement à un autre dans un Recordset](#_core_scrolling_from_one_record_to_another).

- [Dans quelles circonstances le défilement est et n’est pas pris en charge](#_core_when_scrolling_is_supported).

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Défilement d’un enregistrement à un autre

La classe `CRecordset` fournit les fonctions membres `Move` pour le défilement dans un Recordset. Ces fonctions déplacent l’enregistrement actuel par ensembles de lignes. Si vous avez implémenté l’extraction de lignes en bloc, une opération de `Move` repositionne le Recordset en fonction de la taille de l’ensemble de lignes. Si vous n’avez pas implémenté l’extraction de lignes en bloc, un appel à une fonction `Move` repositionne le Recordset d’un enregistrement à chaque fois. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Lors du déplacement dans un jeu d’enregistrements, les enregistrements supprimés peuvent ne pas être ignorés. Pour plus d’informations, consultez la fonction membre [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) .

Outre les fonctions `Move`, `CRecordset` fournit des fonctions membres pour vérifier si vous avez défilé au-delà de la fin ou avant le début de votre Recordset.

Pour déterminer si le défilement est possible dans votre Recordset, appelez la fonction membre `CanScroll`.

#### <a name="to-scroll"></a>Pour faire défiler

1. Transférer un enregistrement ou un ensemble de lignes : appelez la fonction membre [MoveNext](../../mfc/reference/crecordset-class.md#movenext) .

1. Reculer d’un enregistrement ou d’un ensemble de lignes : appelez la fonction membre [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) .

1. Pour le premier enregistrement du Recordset : appelez la fonction membre [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) .

1. Pour le dernier enregistrement dans le jeu d’enregistrements ou dans le dernier ensemble de lignes : appelez la fonction membre [MoveLast](../../mfc/reference/crecordset-class.md#movelast) .

1. *N* enregistrements relatifs à la position actuelle : appelez la fonction membre [Move](../../mfc/reference/crecordset-class.md#move) .

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Pour tester la fin ou le début du Recordset

1. Avez-vous parcouru le dernier enregistrement ? Appelez la fonction membre [IsEOF](../../mfc/reference/crecordset-class.md#iseof) .

1. Avez-vous parcouru le premier enregistrement (déplacement vers l’arrière) ? Appelez la fonction membre [IsBOF](../../mfc/reference/crecordset-class.md#isbof) .

L’exemple de code suivant utilise `IsBOF` et `IsEOF` pour détecter les limites d’un jeu d’enregistrements lors du défilement dans l’une ou l’autre direction.

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

`IsEOF` retourne une valeur différente de zéro si le jeu d’enregistrements est positionné au-delà du dernier enregistrement. `IsBOF` retourne une valeur différente de zéro si le jeu d’enregistrements est positionné avant le premier enregistrement (avant tous les enregistrements). Dans les deux cas, il n’y a aucun enregistrement en cours à utiliser. Si vous appelez `MovePrev` quand `IsBOF` a déjà la valeur TRUE ou si vous appelez `MoveNext` quand `IsEOF` est déjà TRUE, le Framework lève une `CDBException`. Vous pouvez également utiliser `IsBOF` et `IsEOF` pour rechercher un jeu d’enregistrements vide.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Lorsque le défilement est pris en charge

Comme initialement conçu, SQL a uniquement fourni le défilement avant, mais ODBC étend les fonctionnalités de défilement. Le niveau de prise en charge disponible pour le défilement dépend des pilotes ODBC avec lesquels votre application fonctionne, du niveau de conformité de l’API ODBC de votre pilote et de la possibilité de charger la bibliothèque de curseurs ODBC en mémoire. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Vous pouvez contrôler si la bibliothèque de curseurs est utilisée. Consultez les paramètres *bUseCursorLib* et *dwOptions* de [CDatabase :: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  Contrairement aux classes DAO MFC, les classes ODBC MFC ne fournissent pas un ensemble de fonctions de `Find` pour localiser l’enregistrement suivant (ou précédent) qui répond aux critères spécifiés.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset :: CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset :: CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
