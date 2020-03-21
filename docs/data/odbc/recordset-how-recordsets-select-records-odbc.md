---
title: "Recordset : sélection d'enregistrements par les recordsets (ODBC)"
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 4b446d69651cb3cf52bd6c15899d85ed76b319da
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079809"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Recordset : sélection d'enregistrements par les recordsets (ODBC)

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez quand même créer un consommateur manuellement.

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique :

- [Les rôle et options dont vous disposez pour sélectionner des enregistrements](#_core_your_options_in_selecting_records)

- [Comment un recordset construit son instruction SQL et sélectionne des enregistrements](#_core_how_a_recordset_constructs_its_sql_statement)

- [Ce que vous pouvez faire pour personnaliser la sélection](#_core_customizing_the_selection)

Les recordsets sélectionnent des enregistrements à partir d’une source de données par le biais d’un pilote ODBC auquel ils envoient des instructions SQL. L’instruction SQL envoyée dépend de la conception et de l’ouverture de votre classe recordset.

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> Vos options dans la sélection d’enregistrements

Le tableau suivant indique les options dont vous disposez pour sélectionner des enregistrements.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Comment et quand vous pouvez affecter un recordset

|Quand vous|Vous pouvez :|
|--------------|-------------|
|Déclarez la classe recordset avec l’Assistant **Ajout de classe**|Spécifier la table dans laquelle effectuer la sélection.<br /><br /> Spécifier les colonnes à inclure.<br /><br /> Consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Effectuez l’implémentation de la classe recordset|Substituer des fonctions membres comme `OnSetOptions` (avancé) pour définir des options spécifiques de l’application ou pour changer des valeurs par défaut. Spécifiez des membres de données de paramètre si vous souhaitez un recordset paramétrable.|
|Construisez un objet recordset (avant d’appeler `Open`)|Spécifier une condition de recherche (éventuellement composée) en vue de l’utiliser dans une clause **WHERE** qui filtre les enregistrements. Consultez [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Spécifier un ordre de tri en vue de l’utiliser dans une clause **ORDER BY** qui trie les enregistrements. Consultez [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Définir les valeurs des paramètres ajoutés à la classe. Consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

|Exécutez la requête du recordset en appelant `Open`|Spécifier une chaîne SQL personnalisée pour remplacer la chaîne SQL par défaut configurée par l’Assistant. Consultez [CRecordset :: Open](../../mfc/reference/crecordset-class.md#open) dans la *référence* de la bibliothèque de classes et [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

|Appelez `Requery` pour actualiser le recordset avec les valeurs les plus récentes sur la source de données|Spécifier de nouveaux paramètres, filtre ou tri. Consultez [Recordset : rerequête d’un Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Comment un recordset construit son instruction SQL

Quand vous appelez la fonction membre [Open](../../mfc/reference/crecordset-class.md#open) d’un objet recordset, `Open` construit une instruction SQL en utilisant une partie ou la totalité des ingrédients suivants :

- Le paramètre *lpszSQL* passé à `Open`. S’il ne vaut pas NULL, ce paramètre spécifie une chaîne SQL personnalisée entière ou partielle. Le framework analyse la chaîne. Si la chaîne est une instruction **SELECT** SQL ou une instruction **CALL** ODBC, le framework utilise la chaîne comme instruction SQL du recordset. Si la chaîne ne commence pas par « SELECT » ou « {CALL », le framework utilise ce qui est fourni pour construire une clause **FROM** SQL.

- La chaîne retournée par [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Par défaut, il s’agit du nom de la table que vous avez spécifiée pour le recordset dans l’Assistant, mais vous pouvez changer ce que la fonction retourne. Le framework appelle `GetDefaultSQL` : si la chaîne ne commence pas par « SELECT » ou « {CALL », c’est censé être un nom de table, qui est utilisé pour construire la chaîne SQL.

- Les membres de données de champ du recordset, qui doivent être liés à des colonnes spécifiques de la table. Le framework lie les colonnes d’enregistrements aux adresses de ces membres, en les utilisant comme mémoires tampons. Le framework détermine la corrélation des membres de données de champ avec les colonnes de table à partir des appels de fonction [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou Bulk RFX dans la fonction membre [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) du recordset.

- Le [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour le recordset, le cas échéant, contenu dans le membre de données [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter). Le framework utilise cette chaîne pour construire une clause **WHERE** SQL.

- L’ordre de [tri](../../data/odbc/recordset-sorting-records-odbc.md) pour le recordset, le cas échéant, contenu dans le membre de données [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort). Le framework utilise cette chaîne pour construire une clause **ORDER BY** SQL.

   > [!TIP]
   > Pour utiliser la clause **GROUP BY** SQL (et éventuellement la clause **HAVING**), ajoutez-les à la fin de la chaîne de filtre.

- Les valeurs de tout [membre de données de paramètre](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que vous spécifiez pour la classe. Vous définissez les valeurs de paramètre juste avant d’appeler `Open` ou `Requery`. Le framework lie les valeurs de paramètre à des espaces réservés « ? » dans la chaîne SQL. Au moment de la compilation, vous spécifiez la chaîne avec des espaces réservés. Au moment de l’exécution, le framework complète les détails en fonction des valeurs de paramètre que vous passez.

`Open` construit une instruction **SELECT** SQL à partir de ces ingrédients. Consultez [Personnalisation de la sélection](#_core_customizing_the_selection) pour plus d’informations sur la façon dont le framework utilise les ingrédients.

Une fois l’instruction SQL construite, `Open` l’envoie au gestionnaire de pilotes ODBC (et à la bibliothèque de curseurs ODBC si elle est en mémoire), qui à son tour l’envoie au pilote ODBC du SGBD utilisé. Le pilote communique avec le SGBD pour effectuer la sélection sur la source de données et extrait le premier enregistrement. Le framework charge l’enregistrement dans les membres de données de champ du recordset.

Vous pouvez utiliser une combinaison de ces techniques pour ouvrir des [tables](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) et construire une requête basée sur une [jointure](../../data/odbc/recordset-performing-a-join-odbc.md) de plusieurs tables. Au moyen d’une personnalisation supplémentaire, vous pouvez appeler des [requêtes prédéfinies](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procédures stockées), sélectionner des colonnes de table inconnues au moment de la conception et les [lier](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) à des champs du recordset, ou vous pouvez effectuer la plupart des autres tâches d’accès aux données. Concernant les tâches que vous ne pouvez pas effectuer en personnalisant les recordsets, vous pouvez les accomplir en [appelant des fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) ou en exécutant directement des instructions SQL avec [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> Personnalisation de la sélection

En plus de fournir un filtre, un ordre de tri ou des paramètres, vous pouvez effectuer les actions suivantes pour personnaliser la sélection du recordset :

- Passer une chaîne SQL personnalisée dans *lpszSQL* quand vous appelez [Open](../../mfc/reference/crecordset-class.md#open) pour le recordset. Tout ce que vous passez dans *lpsqSQL* est prioritaire sur ce que la fonction membre [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) retourne.

   Pour plus d’informations, consultez [SQL : personnalisation de l’instruction SQL de votre jeu d’enregistrements (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), qui décrit les types d’instructions SQL (ou instructions partielles) que vous pouvez passer à `Open` et ce que l’infrastructure fait avec eux.

    > [!NOTE]
    >  Si la chaîne personnalisée que vous transmettez ne commence pas par « SELECT » ou « {CALL », MFC suppose qu’elle contient un nom de table. Cela concerne également le point suivant.

- Modifier la chaîne que l’Assistant écrit dans la fonction membre `GetDefaultSQL` du recordset. Modifiez le code de la fonction pour changer ce qu’elle retourne. Par défaut, l’Assistant écrit une fonction `GetDefaultSQL` qui retourne un nom de table unique.

   Vous pouvez demander à `GetDefaultSQL` de retourner n’importe quel élément que vous pouvez passer dans le paramètre *lpszSQL* à `Open`. Si vous ne passez pas de chaîne SQL personnalisée dans *lpszSQL*, le framework utilise la chaîne retournée par `GetDefaultSQL`. Au minimum, `GetDefaultSQL` doit retourner un nom de table unique. Mais vous pouvez lui demander de retourner plusieurs noms de tables, une instruction **SELECT** complète, une instruction **CALL** ODBC, etc. Pour obtenir la liste de ce que vous pouvez passer à *lpszSQL* (ou avoir `GetDefaultSQL` retour), consultez [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Si vous effectuez une jointure de deux ou plusieurs tables, réécrivez `GetDefaultSQL` pour personnaliser la liste de tables utilisée dans la clause **FROM** SQL. Pour plus d’informations, consultez [Recordset : exécution d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Lier manuellement des membres de données de champ supplémentaires, par exemple en fonction d’informations que vous obtenez sur le schéma de votre source de données au moment de l’exécution. Vous ajoutez les membres de données de champ à la classe recordset, les appels de fonction [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou Bulk RFX les concernant à la fonction membre [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) et les initialisations des membres de données au constructeur de la classe. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Substituer des fonctions membres du recordset comme `OnSetOptions` pour définir des options spécifiques de l’application ou pour substituer des valeurs par défaut.

Si vous souhaitez baser le recordset sur une instruction SQL complexe, vous devez utiliser une combinaison de ces techniques de personnalisation. Par exemple, vous pouvez utiliser des clauses SQL et des mots clés non directement pris en charge par les recordsets, voire joindre plusieurs tables.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)