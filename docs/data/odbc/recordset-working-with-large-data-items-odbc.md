---
title: "Recordset : utilisation d'éléments de données volumineux (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360599"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset : utilisation d'éléments de données volumineux (ODBC)

Ce sujet s’applique à la fois aux classes MFC ODBC et aux classes MFC DAO.

> [!NOTE]
> Si vous utilisez les classes MFC DAO, gérez vos grands éléments de données avec la classe [CByteArray](../../mfc/reference/cbytearray-class.md) plutôt que la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). Si vous utilisez les classes MFC ODBC avec `CLongBinary` ramage en vrac aller chercher, utilisez plutôt que `CByteArray`. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supposons que votre base de données peut stocker de grandes données, telles que des bitmaps (photographies des employés, cartes, photos de produits, objets OLE, et ainsi de suite). Ce type de données est souvent appelé un grand objet binaire (ou BLOB) parce que:

- Chaque valeur de champ est grande.

- Contrairement aux nombres et autres types de données simples, il n’a pas de taille prévisible.

- Les données sont informes du point de vue de votre programme.

Ce sujet explique le soutien que les classes de base de données fournissent pour travailler avec de tels objets.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Gestion des grands objets

Les records ont deux façons de résoudre la difficulté particulière de gérer les gros objets binaires. Vous pouvez utiliser la classe [CByteArray](../../mfc/reference/cbytearray-class.md) ou vous pouvez utiliser la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). En général, `CByteArray` est le moyen préféré de gérer les grandes données binaires.

`CByteArray`nécessite plus `CLongBinary` de frais généraux que, mais est plus capable, comme décrit dans [la classe CByteArray](#_core_the_cbytearray_class). `CLongBinary`est décrit brièvement dans [The CLongBinary Class](#_core_the_clongbinary_class).

Pour obtenir des `CByteArray` informations détaillées sur l’utilisation pour travailler avec de grands éléments de données, voir [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>Classe CByteArray

`CByteArray`est l’une des classes de collecte MFC. Un `CByteArray` objet stocke un tableau dynamique d’octets — le tableau peut se développer si nécessaire. La classe offre un accès rapide par index, comme avec les tableaux intégrés de C. `CByteArray`objets peuvent être sérialisés et jetés à des fins diagnostiques. La classe fournit aux membres des fonctions pour obtenir et définir des octets spécifiés, insérer et installer des octets, et enlever un octet ou tous les octets. Ces installations facilitent l’analyse des données binaires. Par exemple, si l’objet binaire est un objet OLE, vous devrez peut-être travailler à travers certains octets d’en-tête pour atteindre l’objet réel.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Utilisation de CByteArray dans Recordsets

En donnant à un membre des `CByteArray`données de terrain de votre enregistrement le type, vous fournissez une base fixe à partir de laquelle [RFX](../../data/odbc/record-field-exchange-rfx.md) peut gérer le transfert d’un tel objet entre votre ensemble d’enregistrements et la source de données et à travers lequel vous pouvez manipuler les données à l’intérieur de l’objet. RFX a besoin d’un site spécifique pour les données récupérées, et vous avez besoin d’un moyen d’accéder aux données sous-jacentes.

Pour obtenir des `CByteArray` informations détaillées sur l’utilisation pour travailler avec de grands éléments de données, voir [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>Classe CLongBinary

Un objet [CLongBinary](../../mfc/reference/clongbinary-class.md) est une `HGLOBAL` simple coque autour d’une poignée à un bloc de stockage alloué sur le tas. Lorsqu’il lie une colonne de table contenant un gros `HGLOBAL` objet binaire, RFX alloue la poignée `CLongBinary` lorsqu’elle doit transférer les données au jeu d’enregistrement et stocke la poignée dans le domaine de l’ensemble d’enregistrements.

À son tour, `HGLOBAL` vous `m_hData`utilisez la poignée, , pour travailler avec les données elles-mêmes, en fonction comme vous le feriez sur toutes les données de poignée. C’est là [que CByteArray](../../mfc/reference/cbytearray-class.md) ajoute des capacités.

> [!CAUTION]
> Les objets CLongBinary ne peuvent pas être utilisés comme paramètres dans les appels de fonction. En outre, leur implémentation, qui appelle `::SQLGetData`, ralentit nécessairement les performances de défilement pour un instantané défilement. Cela peut également être vrai `::SQLGetData` lorsque vous utilisez un appel vous-même pour récupérer des colonnes de schéma dynamiques.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)
