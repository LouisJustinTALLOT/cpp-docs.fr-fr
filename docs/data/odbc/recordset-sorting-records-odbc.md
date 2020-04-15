---
title: "Recordset : tri d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366926"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset : tri d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Ce sujet explique comment trier votre dossier. Vous pouvez spécifier une ou plusieurs colonnes sur lesquelles baser le tri, et vous pouvez spécifier l’ordre ascendant ou descendant **(ASC** ou **DESC**; **NCP** est le défaut) pour chaque colonne spécifiée. Par exemple, si vous spécifiez deux colonnes, les enregistrements sont triés d’abord sur la première colonne nommée, puis sur la deuxième colonne nommée. Une clause SQL **ORDER BY** définit une sorte. Lorsque le cadre joint la clause **ORDER BY** à la requête SQL du dossier, la clause contrôle la commande de la sélection.

Vous devez établir l’ordre de tri d’un recordet `Open` après avoir construit l’objet, mais avant d’appeler sa fonction de membre (ou avant d’appeler la `Requery` fonction membre pour un objet enregistreur existant dont `Open` la fonction de membre a été appelée précédemment).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Pour spécifier une commande de tri pour un objet de recordet

1. Construire un nouvel objet de la `Requery` composition des enregistrements (ou préparer à en appeler pour un objet existant).

1. Définissez la valeur du membre [des données m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) de l’objet.

   Le tri est une chaîne non terminée. Il contient le contenu de la clause **ORDER BY,** mais pas le mot clé **ORDER BY**. Par exemple, utilisez :

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Définissez toutes les autres options dont vous avez besoin, comme un filtre, un mode de verrouillage ou des paramètres.

1. Appelez `Open` pour le nouvel `Requery` objet (ou pour un objet existant).

Les enregistrements sélectionnés sont commandés comme spécifié. Par exemple, pour trier un ensemble de dossiers d’étudiants dans l’ordre décroissant par nom de famille, puis prénom, faites ce qui suit :

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Le dossier contient tous les dossiers des élèves, triés par ordre décroissant (Z à A) par nom de famille, puis par prénom.

> [!NOTE]
> Si vous choisissez de remplacer la chaîne SQL par défaut du `Open`recordet en passant votre propre chaîne SQL à , ne définissez pas une sorte si votre chaîne personnalisée a une clause **ORDER BY.**

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : paramétrage d'un recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset : filtrage d'enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
