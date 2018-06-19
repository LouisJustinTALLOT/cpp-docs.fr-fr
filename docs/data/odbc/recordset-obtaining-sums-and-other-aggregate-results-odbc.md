---
title: 'Recordset : Calculs de totaux et autres résultats de regroupement (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4aa6de58e7e2c530a7a353281ba5af747f48cd4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092071"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Recordset : calculs de totaux et autres résultats de regroupement (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment obtenir des résultats de regroupement à l’aide de ce qui suit [SQL](../../data/odbc/sql.md) mots clés :  
  
-   **SOMME** calcule le total des valeurs dans une colonne avec un type de données numérique.  
  
-   **MIN** extrait la plus petite valeur dans une colonne avec un type de données numérique.  
  
-   **MAX** extrait la plus grande valeur dans une colonne avec un type de données numérique.  
  
-   **AVG** calcule la valeur moyenne de toutes les valeurs dans une colonne avec un type de données numérique.  
  
-   **NOMBRE** compte le nombre d’enregistrements dans une colonne de tout type de données.  
  
 Vous utilisez ces fonctions SQL pour obtenir des informations statistiques sur les enregistrements dans une source de données et non pour extraire des enregistrements à partir de la source de données. Le jeu d’enregistrements est créé habituellement se compose d’un seul enregistrement (si toutes les colonnes sont des regroupements) qui contient une valeur. (Il peut y avoir plusieurs enregistrements si vous avez utilisé un **GROUP BY** clause.) Cette valeur est le résultat du calcul ou d’extraction effectuée par la fonction SQL.  
  
> [!TIP]
>  Pour ajouter une SQL **GROUP BY** clause (et éventuellement un **HAVING** clause) à votre instruction SQL, ajoutez-la à la fin de **m_strFilter**. Par exemple :  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 Vous pouvez limiter le nombre d’enregistrements qui que vous permet d’obtenir des résultats de regroupement en filtrant et en triant les colonnes.  
  
> [!CAUTION]
>  Certains opérateurs d’agrégation retournent un autre type de données à partir des colonnes sur lesquelles ils sont regroupés.  
  
-   **SOMME** et **AVG** peut retourner le type de données immédiatement supérieur (par exemple, l’appel avec `int` retourne **LONG** ou **double**).  
  
-   **NOMBRE de** retourne généralement **LONG** , quelle que soit le type de colonne cible.  
  
-   **MAX** et **MIN** retournent le même type de données que les colonnes utilisées pour le calcul.  
  
     Par exemple, le **ajouter une classe** crée `long` `m_lSales` pour prendre en charge de la colonne Sales, mais vous devez remplacer ceci avec un `double m_dblSumSales` membre de données pour recevoir le résultat du regroupement. Lisez l'exemple suivant.  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Pour obtenir un résultat d’agrégation pour un jeu d’enregistrements  
  
1.  Créer un jeu d’enregistrements, comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) contenant les colonnes à partir de laquelle vous souhaitez obtenir des résultats de regroupement.  
  
2.  Modifier la [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) fonction du jeu d’enregistrements. Remplacez la chaîne représentant le nom de colonne (le deuxième argument de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) appels de fonction) avec une chaîne qui représente la fonction d’agrégation sur la colonne. Par exemple, remplacez :  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     avec :  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  Ouvrez le jeu d’enregistrements. Le résultat de l’opération d’agrégation est conservé dans `m_dblSumSales`.  
  
> [!NOTE]
>  En fait, l’Assistant attribue des noms de membres de données sans préfixes Hongrois. Par exemple, l’Assistant génère `m_Sales` pour la colonne Sales, plutôt que `m_lSales` nom utilisé précédemment, à titre d’illustration.  
  
 Si vous utilisez un [CRecordView](../../mfc/reference/crecordview-class.md) de classes pour afficher les données, vous devez modifier l’appel de fonction DDX pour afficher la nouvelle valeur du membre de données ; dans ce cas, la modifier à partir de :  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 À :  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)