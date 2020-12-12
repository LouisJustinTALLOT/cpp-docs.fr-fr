---
description: 'En savoir plus sur : Recordset : utilisation d’éléments de données volumineux (ODBC)'
title: "Recordset : utilisation d'éléments de données volumineux (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 7a4ca6de9c0b5be32626c8ca3c7c66cc516057e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204366"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset : utilisation d'éléments de données volumineux (ODBC)

Cette rubrique s’applique aux classes ODBC MFC et aux classes DAO MFC.

> [!NOTE]
> Si vous utilisez les classes DAO MFC, gérez vos éléments de données volumineux avec la classe [CByteArray](../../mfc/reference/cbytearray-class.md) plutôt que la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). Si vous utilisez les classes ODBC MFC avec l’extraction de lignes en bloc, utilisez `CLongBinary` plutôt que `CByteArray` . Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supposons que votre base de données peut stocker des éléments de données volumineux, tels que des bitmaps (photographies d’employés, cartes, images de produits, objets OLE, etc.). Ce type de données est souvent appelé Large Object binaire (ou BLOB), car :

- Chaque valeur de champ est volumineuse.

- Contrairement aux nombres et autres types de données simples, la taille n’est pas prévisible.

- Les données sont non conformes du point de vue de votre programme.

Cette rubrique explique la prise en charge fournie par les classes de base de données pour travailler avec ces objets.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a> Gestion des objets volumineux

Les jeux d’enregistrements offrent deux moyens de résoudre les problèmes particuliers liés à la gestion d’objets binaires volumineux. Vous pouvez utiliser la classe [CByteArray](../../mfc/reference/cbytearray-class.md) ou vous pouvez utiliser la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). En général, `CByteArray` est la meilleure façon de gérer des données binaires volumineuses.

`CByteArray` nécessite un temps de traitement supérieur à `CLongBinary` , mais est plus efficace, comme décrit dans [la classe CByteArray](#_core_the_cbytearray_class). `CLongBinary` est décrit brièvement dans [la classe CLongBinary](#_core_the_clongbinary_class).

Pour plus d’informations sur l’utilisation `CByteArray` de pour utiliser des éléments de données volumineux, consultez la [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a> Classe CByteArray

`CByteArray` est l’une des classes de collection MFC. Un `CByteArray` objet stocke un tableau dynamique d’octets : le tableau peut croître si nécessaire. La classe fournit un accès rapide par index, comme avec les tableaux C++ intégrés. `CByteArray` les objets peuvent être sérialisés et vidés à des fins de diagnostic. La classe fournit des fonctions membres pour l’obtention et la définition d’octets spécifiés, l’insertion et l’ajout d’octets et la suppression d’un octet ou de tous les octets. Ces fonctionnalités facilitent l’analyse des données binaires. Par exemple, si l’objet binaire est un objet OLE, vous devrez peut-être utiliser des octets d’en-tête pour atteindre l’objet réel.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a> Utilisation de CByteArray dans les recordsets

En attribuant le type à un membre de données de champ de votre jeu d’enregistrements `CByteArray` , vous fournissez une base fixe à partir de laquelle [RFX](../../data/odbc/record-field-exchange-rfx.md) peut gérer le transfert d’un tel objet entre votre Recordset et la source de données, et vous permet de manipuler les données à l’intérieur de l’objet. RFX a besoin d’un site spécifique pour les données récupérées, et vous avez besoin d’un moyen d’accéder aux données sous-jacentes.

Pour plus d’informations sur l’utilisation `CByteArray` de pour utiliser des éléments de données volumineux, consultez la [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a> CLongBinary (classe)

Un objet [CLongBinary](../../mfc/reference/clongbinary-class.md) est un shell simple autour d’un `HGLOBAL` handle vers un bloc de stockage alloué sur le tas. Lorsqu’il lie une colonne de table contenant un objet binaire volumineux, RFX alloue le `HGLOBAL` handle lorsqu’il doit transférer les données vers le Recordset et stocke le handle dans le `CLongBinary` champ du Recordset.

À son tour, vous utilisez le `HGLOBAL` handle, `m_hData` , pour travailler avec les données proprement dites, en opérant dessus comme vous le feriez sur n’importe quelle donnée de handle. C’est là que [CByteArray](../../mfc/reference/cbytearray-class.md) ajoute des fonctionnalités.

> [!CAUTION]
> Les objets CLongBinary ne peuvent pas être utilisés en tant que paramètres dans les appels de fonction. En outre, leur implémentation, qui appelle `::SQLGetData` , ralentit nécessairement les performances de défilement pour un instantané avec défilement. Cela peut également être le cas lorsque vous utilisez un `::SQLGetData` appel vous-même pour récupérer des colonnes de schéma dynamique.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : calculs de totaux et autres résultats d’agrégation (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[RFX (Record Field Exchange)](../../data/odbc/record-field-exchange-rfx.md)
