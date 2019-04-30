---
title: 'Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: e10f2e1574dae234d98d210784d4a8ddef3bb57e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397781"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment obtenir des résultats de regroupement à l’aide de ce qui suit [SQL](../../data/odbc/sql.md) mots clés :

- **SOMME** calcule le total des valeurs dans une colonne avec un type de données numérique.

- **MIN** extrait la plus petite valeur dans une colonne avec un type de données numérique.

- **MAX** extrait la plus grande valeur dans une colonne avec un type de données numérique.

- **AVG** calcule une valeur moyenne de toutes les valeurs dans une colonne avec un type de données numérique.

- **NOMBRE** comptabilise le nombre d’enregistrements dans une colonne de n’importe quel type de données.

Vous utilisez ces fonctions SQL pour obtenir des informations statistiques sur les enregistrements dans une source de données plutôt que pour extraire des enregistrements à partir de la source de données. Le jeu d’enregistrements qui est généralement créée se compose d’un seul enregistrement (si toutes les colonnes sont des agrégats) qui contient une valeur. (Il peut y avoir plusieurs enregistrements si vous avez utilisé un **GROUP BY** clause.) Cette valeur est le résultat du calcul ou d’extraction effectuée par la fonction SQL.

> [!TIP]
>  Pour ajouter une instance SQL **GROUP BY** clause (et éventuellement un **HAVING** clause) à votre instruction SQL, ajoutez-le à la fin de `m_strFilter`. Exemple :

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Vous pouvez limiter le nombre d’enregistrements qui que vous permet d’obtenir des résultats de regroupement en filtrant et en triant les colonnes.

> [!CAUTION]
>  Certains opérateurs d’agrégation retournent un autre type de données à partir des colonnes sur lesquelles ils sont regroupés.

- **SOMME** et **AVG** peut retourner le type de données immédiatement supérieur (par exemple, l’appel avec `int` retourne **LONG** ou **double**).

- **NOMBRE** retourne généralement **LONG** , quel que soit le type de colonne cible.

- **MAX** et **MIN** retournent le même type de données que les colonnes utilisées pour le calcul.

     Par exemple, le **ajouter une classe** Assistant crée `long` `m_lSales` pour prendre en charge de la colonne Sales, mais vous devez remplacer ceci avec un `double m_dblSumSales` membre de données pour prendre en charge le résultat du regroupement. Lisez l'exemple suivant.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Pour obtenir un résultat d’agrégation pour un jeu d’enregistrements

1. Créer un jeu d’enregistrements, comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) contenant les colonnes à partir de laquelle vous souhaitez obtenir des résultats de regroupement.

1. Modifier le [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) (fonction) pour le jeu d’enregistrements. Remplacez la chaîne représentant le nom de colonne (le deuxième argument de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) appels de fonction) avec une chaîne qui représente la fonction d’agrégation sur la colonne. Par exemple, remplacez :

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     Par :

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Ouvrez le jeu d’enregistrements. Le résultat de l’opération d’agrégation est conservé dans `m_dblSumSales`.

> [!NOTE]
>  En fait, l’Assistant attribue des noms de membre de données sans préfixes Hongrois. Par exemple, l’Assistant génère `m_Sales` pour la colonne Sales, plutôt que `m_lSales` nom utilisé précédemment à titre d’illustration.

Si vous utilisez un [CRecordView](../../mfc/reference/crecordview-class.md) pour afficher les données de classe, vous devez modifier l’appel de fonction DDX pour afficher la nouvelle valeur du membre de données ; dans ce cas, sa modification de :

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

À :

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)