---
title: 'Recordset : Tri d’enregistrements (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 831f21901186ed0ae010b0f332327eefcba94b51
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024658"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset : Tri d’enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment trier le jeu d’enregistrements. Vous pouvez spécifier une ou plusieurs colonnes sur lequel baser le tri, et vous pouvez spécifier d’ordre croissant ou décroissant (**ASC** ou **DESC**; **ASC** est la valeur par défaut) pour chaque spécifié la colonne. Par exemple, si vous spécifiez deux colonnes, les enregistrements sont d’abord triés sur la première colonne, puis sur la deuxième colonne nommée. SQL **ORDER BY** clause définit un tri. Lorsque le framework ajoute la **ORDER BY** clause to SQL du jeu d’enregistrements de requête, les contrôles de la clause de tri à la sélection.

Vous devez établir ordre de tri d’un jeu d’enregistrements après avoir construit l’objet mais avant d’appeler ses `Open` fonction membre (ou avant d’appeler le `Requery` fonction membre pour un jeu d’enregistrements existant de l’objet dont la propriété `Open` fonction membre a été appelée au préalable).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Pour spécifier un ordre de tri pour un objet recordset

1. Construisez un nouvel objet recordset (ou préparez l’appel `Requery` pour un).

1. Définissez la valeur de l’objet [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) membre de données.

   Le tri est une chaîne se terminant par null. Il contient le contenu de la **ORDER BY** clause, mais pas le mot clé **ORDER BY**. Par exemple, utilisez :

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Définissez les autres options que vous avez besoin, comme un filtre, le mode de verrouillage ou paramètres.

1. Appelez `Open` pour le nouvel objet (ou `Requery` pour un objet existant).

Les enregistrements sélectionnés sont classés comme spécifié. Par exemple, pour trier un ensemble d’enregistrements d’étudiants dans l’ordre décroissant par nom de famille, puis les prénoms, procédez comme suit :

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Le jeu d’enregistrements contient tous les enregistrements d’étudiants, triés par ordre décroissant (Z à A) par nom de famille, puis par prénom.

> [!NOTE]
>  Si vous choisissez de remplacer la chaîne SQL par défaut du jeu d’enregistrements en passant votre propre chaîne SQL à `Open`, ne définissez pas de tri si votre chaîne personnalisée contient une **ORDER BY** clause.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)