---
description: 'En savoir plus sur : Recordset : tri d’enregistrements (ODBC)'
title: "Recordset : tri d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: fbf2ef3c42061bac9b41550a0c44a20f68c099b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204418"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset : tri d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment trier votre jeu d’enregistrements. Vous pouvez spécifier une ou plusieurs colonnes sur lesquelles baser le tri, et vous pouvez spécifier l’ordre croissant ou décroissant (**ASC** ou **desc**). **ASC** est la valeur par défaut) pour chaque colonne spécifiée. Par exemple, si vous spécifiez deux colonnes, les enregistrements sont d’abord triés sur la première colonne nommée, puis sur la deuxième colonne nommée. Une clause SQL **order by** définit un tri. Lorsque l’infrastructure ajoute la clause **order by** à la requête SQL du Recordset, la clause contrôle le classement de la sélection.

Vous devez établir l’ordre de tri d’un jeu d’enregistrements après avoir construit l’objet, mais avant d’appeler `Open` la fonction membre (ou avant d’appeler la `Requery` fonction membre pour un objet Recordset existant dont la `Open` fonction membre a été appelée précédemment).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Pour spécifier un ordre de tri pour un objet Recordset

1. Construit un nouvel objet Recordset (ou prépare l’appel à `Requery` un objet existant).

1. Définissez la valeur du membre de données [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) de l’objet.

   Le tri est une chaîne terminée par le caractère null. Elle contient le contenu de la clause **order by** , mais pas le mot clé **order by**. Par exemple, utilisez :

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Définissez les autres options dont vous avez besoin, telles qu’un filtre, un mode de verrouillage ou des paramètres.

1. Appelez `Open` pour le nouvel objet (ou `Requery` pour un objet existant).

Les enregistrements sélectionnés sont triés comme spécifié. Par exemple, pour trier un ensemble d’enregistrements d’élèves dans l’ordre décroissant par nom, puis par nom, procédez comme suit :

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Le jeu d’enregistrements contient tous les enregistrements d’étudiants, triés dans l’ordre décroissant (Z à A) par nom, puis par prénom.

> [!NOTE]
> Si vous choisissez de remplacer la chaîne SQL par défaut du Recordset en passant votre propre chaîne SQL à `Open` , ne définissez pas de tri si votre chaîne personnalisée contient une clause **order by** .

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
