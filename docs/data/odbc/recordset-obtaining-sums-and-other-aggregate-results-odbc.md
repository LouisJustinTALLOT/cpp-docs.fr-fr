---
title: 'Recordset : calcul de totaux et obtention d’autres résultats d’agrégation (ODBC)'
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
ms.openlocfilehash: 29906366e6e9a5a852fcf40d9e7ecc8593d1b0b0
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707843"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Recordset : calcul de totaux et obtention d’autres résultats d’agrégation (ODBC)

> [!NOTE] 
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toutefois créer un consommateur manuellement.

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment obtenir les résultats d’agrégation avec les mots clés [SQL](../../data/odbc/sql.md) suivants :

- **SUM** calcule le total des valeurs dans une colonne ayant un type de données numérique.

- **MIN** extrait la plus petite valeur dans une colonne ayant un type de données numérique.

- **MAX** extrait la plus grande valeur dans une colonne ayant un type de données numérique.

- **AVG** calcule une valeur moyenne de toutes les valeurs dans une colonne ayant un type de données numérique.

- **COUNT** comptabilise le nombre d’enregistrements dans une colonne de n’importe quel type de données.

Ces fonctions SQL s’utilisent pour obtenir des informations statistiques sur les enregistrements contenus dans une source de données plutôt que pour extraire des enregistrements de la source de données. Le recordset créé se compose généralement d’un seul enregistrement (si toutes les colonnes sont des agrégats) contenant une valeur. (Il peut y avoir plusieurs enregistrements si vous avez utilisé une clause **GROUP BY**.) Cette valeur est le résultat de l’opération de calcul ou d’extraction effectuée par la fonction SQL.

> [!TIP]
>  Quand vous ajoutez une clause SQL **GROUP BY** (et éventuellement une clause **HAVING**) à l’instruction SQL, placez-la à la fin de `m_strFilter`. Par exemple :

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Vous pouvez limiter le nombre d’enregistrements utilisés pour obtenir des résultats d’agrégation en filtrant et en triant les colonnes.

> [!CAUTION]
>  Certains opérateurs d’agrégation retournent un type de données différent des colonnes sur lesquelles porte l’agrégation.

- **SUM** et **AVG** peuvent retourner un type de données de longueur immédiatement supérieure (par exemple, l’appel avec `int` retourne le type **LONG** ou **double**).

- **COUNT** retourne généralement le type **LONG** indépendamment du type de la colonne cible.

- **MAX** et **MIN** retournent le même type de données que les colonnes utilisées pour le calcul.

     Par exemple, l’Assistant **Ajouter une classe** crée `long` `m_lSales` dans le cas d’une colonne Sales, mais vous devez le remplacer par un membre de données `double m_dblSumSales` pouvant contenir le résultat de l’agrégation. Lisez l'exemple suivant.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Pour obtenir un résultat d’agrégation à partir d’un recordset

1. En suivant les étapes décrites dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md), créez un recordset contenant les colonnes à partir desquelles vous souhaitez obtenir un résultat d’agrégation.

1. Modifiez la fonction [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pour le recordset. Remplacez la chaîne représentant le nom de colonne (le deuxième argument dans les appels de fonction [RFX](../../data/odbc/record-field-exchange-using-rfx.md)) par une chaîne représentant la fonction d’agrégation appliquée sur la colonne. Par exemple, remplacez :

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     Par :

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Ouvrez le recordset. Le résultat de l’opération d’agrégation est conservé dans `m_dblSumSales`.

> [!NOTE]
>  En fait, l’Assistant attribue des noms sans préfixe hongrois aux membres de données. Par exemple, l’Assistant génère le nom `m_Sales` pour la colonne Sales à la place du nom `m_lSales` utilisé précédemment à titre d’illustration.

Si vous utilisez une classe [CRecordView](../../mfc/reference/crecordview-class.md) pour afficher les données, vous devez modifier l’appel de fonction DDX pour afficher la nouvelle valeur du membre de données, qui ici a changé de :

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