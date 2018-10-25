---
title: 'Recordset : Défilement (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f8b5107f6e264c5d9915e809c9d198fd4cc4ba24
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053238"
---
# <a name="recordset-scrolling-odbc"></a>Recordset : défilement (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Après avoir ouvert un jeu d’enregistrements, vous avez besoin pour accéder aux enregistrements pour afficher les valeurs, effectuer des calculs, générer des rapports et ainsi de suite. Défilement permet de que passer d’un enregistrement à l’autre au sein de votre jeu d’enregistrements.

Cette rubrique explique :

- [Comment passer d’un enregistrement à l’autre dans un jeu d’enregistrements](#_core_scrolling_from_one_record_to_another).

- [Dans quels cas le défilement est n’est pas pris en charge](#_core_when_scrolling_is_supported).

##  <a name="_core_scrolling_from_one_record_to_another"></a> Défilement d’un enregistrement à un autre

Classe `CRecordset` fournit le `Move` fonctions membre pour faire défiler un jeu d’enregistrements. Ces fonctions déplacent l’enregistrement actif en ensembles de lignes. Si vous avez implémenté l’extraction de lignes en bloc, un `Move` opération repositionne le jeu d’enregistrements en fonction de la taille de l’ensemble de lignes. Si vous n’avez pas implémenté l’extraction, un appel à de lignes en bloc un `Move` fonction repositionne le jeu d’enregistrements en un seul enregistrement chaque fois. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, enregistrements supprimés ne peuvent pas être ignorés. Pour plus d’informations, consultez le [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) fonction membre.

Outre le `Move` fonctions, `CRecordset` fournit des fonctions membres pour vérifier si vous avez atteint la fin ou le début de votre jeu d’enregistrements.

Pour déterminer si le défilement est possible dans votre jeu d’enregistrements, appelez le `CanScroll` fonction membre.

#### <a name="to-scroll"></a>Pour faire défiler

1. Transférer un enregistrement ou un ensemble de lignes : appeler le [MoveNext](../../mfc/reference/crecordset-class.md#movenext) fonction membre.

1. Reculer d’un enregistrement ou un ensemble de lignes : appeler le [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) fonction membre.

1. Le premier enregistrement dans le jeu d’enregistrements : appelez le [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) fonction membre.

1. Pour le dernier enregistrement dans le jeu d’enregistrements ou pour le dernier ensemble de lignes : appeler le [MoveLast](../../mfc/reference/crecordset-class.md#movelast) fonction membre.

1. *N* enregistrements par rapport à la position actuelle : appelez le [déplacer](../../mfc/reference/crecordset-class.md#move) fonction membre.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Pour tester la fin ou le début de l’objet recordset

1. Vous avez atteint le dernier enregistrement ? Appelez le [IsEOF](../../mfc/reference/crecordset-class.md#iseof) fonction membre.

1. Vous avez atteint le premier enregistrement (déplacement vers l’arrière) Appelez le [IsBOF](../../mfc/reference/crecordset-class.md#isbof) fonction membre.

Le code suivant exemple utilise `IsBOF` et `IsEOF` pour détecter les limites d’un jeu d’enregistrements lors du défilement dans les deux sens.

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

`IsEOF` Retourne une valeur différente de zéro si le jeu d’enregistrements est positionné au-delà du dernier enregistrement. `IsBOF` Retourne une valeur différente de zéro si le jeu d’enregistrements est positionné avant le premier enregistrement (avant tous les enregistrements). Dans les deux cas, il n’existe aucun enregistrement actif à utiliser. Si vous appelez `MovePrev` lorsque `IsBOF` est déjà TRUE ou appeler `MoveNext` lorsque `IsEOF` est déjà TRUE, le framework lève une `CDBException`. Vous pouvez également utiliser `IsBOF` et `IsEOF` à vérifier pour un jeu d’enregistrements vide.

Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="_core_when_scrolling_is_supported"></a> Lorsque le défilement est pris en charge

Conçue à l’origine, SQL fourni uniquement en avant le défilement, mais ODBC étend les capacités de défilement. Le niveau de prise en charge pour le défilement disponible varie selon les pilotes ODBC de votre application fonctionne avec le niveau de conformité de votre pilote ODBC API et si la bibliothèque de curseurs ODBC est chargée en mémoire. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Vous pouvez contrôler si la bibliothèque de curseurs est utilisée. Consultez le *bUseCursorLib* et *dwOptions* paramètres [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  Contrairement aux classes DAO MFC, les classes ODBC MFC ne fournissent pas d’un ensemble de `Find` fonctions pour rechercher l’enregistrement suivant (ou précédent) qui répond aux critères spécifiés.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)