---
description: 'En savoir plus sur : Recordset : calculs de totaux et autres résultats d’agrégation (ODBC)'
title: 'Recordset : calculs de totaux et autres résultats de regroupement (ODBC)'
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
ms.openlocfilehash: 10a2ef3b013d9eba0d9733cc321591ae8d6681f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136484"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Recordset : calculs de totaux et autres résultats de regroupement (ODBC)

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer un consommateur manuellement.

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment obtenir les résultats d’agrégation avec les mots clés [SQL](../../data/odbc/sql.md) suivants :

- **SUM** calcule le total des valeurs dans une colonne ayant un type de données numérique.

- **MIN** extrait la plus petite valeur dans une colonne ayant un type de données numérique.

- **MAX** extrait la plus grande valeur dans une colonne ayant un type de données numérique.

- **AVG** calcule une valeur moyenne de toutes les valeurs dans une colonne ayant un type de données numérique.

- **COUNT** comptabilise le nombre d’enregistrements dans une colonne de n’importe quel type de données.

Ces fonctions SQL s’utilisent pour obtenir des informations statistiques sur les enregistrements contenus dans une source de données plutôt que pour extraire des enregistrements de la source de données. Le recordset créé se compose généralement d’un seul enregistrement (si toutes les colonnes sont des agrégats) contenant une valeur. (Il peut y avoir plus d’un enregistrement si vous avez utilisé une clause **Group by** .) Cette valeur est le résultat du calcul ou de l’extraction effectué par la fonction SQL.

> [!TIP]
> Quand vous ajoutez une clause SQL **GROUP BY** (et éventuellement une clause **HAVING**) à l’instruction SQL, placez-la à la fin de `m_strFilter`. Par exemple :

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Vous pouvez limiter le nombre d’enregistrements utilisés pour obtenir des résultats d’agrégation en filtrant et en triant les colonnes.

> [!CAUTION]
> Certains opérateurs d’agrégation retournent un type de données différent des colonnes sur lesquelles porte l’agrégation.

- **Sum** et **AVG** peuvent retourner le plus grand type de données suivant (par exemple, l’appel de avec **`int`** retourne une **valeur long** ou **`double`** ).

- **COUNT** retourne généralement le type **LONG** indépendamment du type de la colonne cible.

- **MAX** et **MIN** retournent le même type de données que les colonnes utilisées pour le calcul.

     Par exemple, l’Assistant **Ajouter une classe** crée **`long`** `m_lSales` pour s’adapter à une colonne sales, mais vous devez le remplacer par un `double m_dblSumSales` membre de données pour prendre en charge le résultat de l’agrégat. Consultez l’exemple qui suit.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Pour obtenir un résultat d’agrégation à partir d’un recordset

1. En suivant les étapes décrites dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md), créez un recordset contenant les colonnes à partir desquelles vous souhaitez obtenir un résultat d’agrégation.

1. Modifiez la fonction [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pour le recordset. Remplacez la chaîne représentant le nom de colonne (le deuxième argument dans les appels de fonction [RFX](../../data/odbc/record-field-exchange-using-rfx.md)) par une chaîne représentant la fonction d’agrégation appliquée sur la colonne. Par exemple, remplacez :

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     par :

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Ouvrez le recordset. Le résultat de l’opération d’agrégation est conservé dans `m_dblSumSales`.

> [!NOTE]
> En fait, l’Assistant attribue des noms sans préfixe hongrois aux membres de données. Par exemple, l’Assistant génère le nom `m_Sales` pour la colonne Sales à la place du nom `m_lSales` utilisé précédemment à titre d’illustration.

Si vous utilisez une classe [CRecordView](../../mfc/reference/crecordview-class.md) pour afficher les données, vous devez modifier l’appel de fonction DDX pour afficher la nouvelle valeur du membre de données, qui ici a changé de :

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

Par :

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
