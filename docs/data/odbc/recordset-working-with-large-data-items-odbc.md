---
title: 'Recordset : Utilisation des éléments de données volumineux (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 3ba8d4af5b0781c425dd3b1223e2208b279f055e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033042"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset : Utilisation des éléments de données volumineux (ODBC)

Cette rubrique s’applique aux classes ODBC MFC et les classes DAO MFC.

> [!NOTE]
>  Si vous utilisez les classes DAO MFC, gérez vos éléments de données volumineux avec la classe [CByteArray](../../mfc/reference/cbytearray-class.md) au lieu de la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). Si vous utilisez les classes ODBC MFC avec l’extraction de lignes en bloc, utilisez `CLongBinary` plutôt que `CByteArray`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supposons que votre base de données peut stocker de grands fragments de données, telles que les bitmaps (photos des employés, cartes, images de produits, les objets OLE et ainsi de suite). Ce type de données est souvent appelé un objet binaire volumineux (ou BLOB), car :

- Chaque valeur de champ est grande.

- Contrairement aux nombres et autres types de données simples, il n’a aucune taille prévisible.

- Les données sont sans formless du point de vue de votre programme.

Cette rubrique explique quelle prise en charge fournissent les classes de base de données pour travailler avec ces objets.

##  <a name="_core_managing_large_objects"></a> La gestion des objets volumineux

Jeux d’enregistrements ont deux façons de résoudre la difficulté de la gestion des objets binaires volumineux. Vous pouvez utiliser la classe [CByteArray](../../mfc/reference/cbytearray-class.md) ou vous pouvez utiliser la classe [CLongBinary](../../mfc/reference/clongbinary-class.md). En règle générale, `CByteArray` est la meilleure méthode pour gérer des données binaires volumineuses.

`CByteArray` nécessite un traitement plus que `CLongBinary` mais n’est plus performante, comme décrit dans [CByteArray, classe](#_core_the_cbytearray_class). `CLongBinary` Décrit brièvement dans [classe CLongBinary](#_core_the_clongbinary_class).

Pour plus d’informations sur l’utilisation de `CByteArray` pour travailler avec des éléments de données volumineux, consultez [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_cbytearray_class"></a> CByteArray, classe

`CByteArray` est une des classes de collection MFC. Un `CByteArray` objet stocke un tableau dynamique d’octets, le tableau peut augmenter si nécessaire. La classe fournit un accès rapide par index, comme avec les tableaux C++ intégrés. `CByteArray` les objets peuvent être sérialisés et vidées pour faciliter le diagnostic. La classe fournit des fonctions de membre pour l’obtention et définition d’octets spécifié, insertion et ajouter des octets et supprimer un octet ou tous les octets. Ces fonctions facilitent l’analyse des données binaires. Par exemple, si l’objet binaire est un objet OLE, vous devrez peut-être fonctionne par le biais des octets d’en-tête pour atteindre l’objet réel.

##  <a name="_core_using_cbytearray_in_recordsets"></a> Utilisation de CByteArray dans les Recordsets

En donnant un membre de données de champ de votre jeu d’enregistrements de type `CByteArray`, vous fournissez une base fixe à partir de laquelle [RFX](../../data/odbc/record-field-exchange-rfx.md) peut gérer le transfert d’un tel objet entre votre jeu d’enregistrements et de la source de données et grâce à laquelle vous pouvez manipuler la données à l’intérieur de l’objet. RFX a besoin d’un site spécifique pour les données récupérées, et que vous avez besoin d’un moyen pour accéder aux données sous-jacentes.

Pour plus d’informations sur l’utilisation de `CByteArray` pour travailler avec des éléments de données volumineux, consultez [Note technique 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_clongbinary_class"></a> CLongBinary (classe)

Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objet est un interpréteur de commandes simple autour d’un `HGLOBAL` handle vers un bloc de stockage alloué sur le tas. Quand il lie une colonne de table contenant un objet binaire volumineux, RFX alloue le `HGLOBAL` gérer lorsqu’il doit transférer les données vers le recordset et stocke le handle dans le `CLongBinary` champ du recordset.

À son tour, vous utilisez le `HGLOBAL` gérer, `m_hData`, pour travailler avec les données elles-mêmes, comme vous sur n’importe quel manipuliez des données. C’est là où [CByteArray](../../mfc/reference/cbytearray-class.md) ajoute des fonctionnalités.

> [!CAUTION]
>  Les objets CLongBinary ne peut pas être utilisés en tant que paramètres dans les appels de fonction. En outre, leur implémentation, qui appelle `::SQLGetData`, nécessairement ralentit les performances de défilement pour un instantané à défilement. Cela peut également être le cas lorsque vous utilisez un `::SQLGetData` appeler vous-même pour récupérer les colonnes de schéma dynamique.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)