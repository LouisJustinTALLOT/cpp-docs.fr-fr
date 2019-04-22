---
title: 'Recordset : La sélection de jeux d’enregistrements d’enregistrements (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 310481a6ea6637de817bf29d528cbdfe70ae70db
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041323"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Recordset : La sélection de jeux d’enregistrements d’enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique :

- [Votre rôle et options de sélection des enregistrements](#_core_your_options_in_selecting_records).

- [Comment un recordset construit son instruction SQL et sélectionne les enregistrements](#_core_how_a_recordset_constructs_its_sql_statement).

- [Ce que vous pouvez faire pour personnaliser la sélection](#_core_customizing_the_selection).

Jeux d’enregistrements de sélectionner des enregistrements à partir d’une source de données via un pilote ODBC en envoyant des instructions SQL au pilote. L’instruction SQL envoyée dépend de la conception et ouvrez votre classe de jeu d’enregistrements.

##  <a name="_core_your_options_in_selecting_records"></a> Vos Options de sélection des enregistrements

Le tableau suivant répertorie les options de sélection des enregistrements.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Quand et comment vous pouvez affecter un jeu d’enregistrements

|Lorsque vous|Vous pouvez|
|--------------|-------------|
|Déclarer la classe de jeu d’enregistrements avec le **ajouter une classe** Assistant|Spécifier la table à sélectionner à partir de.<br /><br /> Spécifiez les colonnes à inclure.<br /><br /> Consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Effectuez votre implémentation de classe de jeu d’enregistrements|Substituer des fonctions membres telles que `OnSetOptions` (Avancé) pour définir des options spécifiques à l’application ou pour modifier les valeurs par défaut. Spécifier les membres de données de paramètre si vous souhaitez un jeu d’enregistrements paramétrable.|
|Construisez un objet recordset (avant d’appeler `Open`)|Spécifiez une condition de recherche (éventuellement composée) pour une utilisation dans un **où** clause qui filtre les enregistrements. Consultez [jeu d’enregistrements : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Spécifier un ordre de tri pour une utilisation dans un **ORDER BY** clause qui trie les enregistrements. Consultez [jeu d’enregistrements : Tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Définir les valeurs des paramètres ajoutés à la classe. Consultez [jeu d’enregistrements : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Exécuter la requête du recordset en appelant `Open`| Spécifiez une chaîne SQL personnalisée pour remplacer la chaîne SQL par défaut configurée par l’Assistant. Consultez [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) dans le *référence de bibliothèque de classe* et [SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

| Appelez `Requery` pour actualiser le jeu d’enregistrements avec les valeurs les plus récentes sur la source de données | Spécifiez les nouveaux paramètres, filtrer ou trier. Consultez [jeu d’enregistrements : Actualisation d’un jeu d’enregistrements (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Comment un Recordset construit son instruction SQL

Lorsque vous appelez un objet recordset [Open](../../mfc/reference/crecordset-class.md#open) fonction membre, `Open` construit une instruction SQL à l’aide de tout ou partie des éléments suivants :

- Le *lpszSQL* paramètre passé à `Open`. Si non NULL, ce paramètre spécifie une chaîne SQL personnalisée ou une partie d’un. Le framework analyse la chaîne. Si la chaîne est une instance SQL **sélectionnez** instruction ou une application ODBC **appeler** instruction, le framework utilise la chaîne comme instruction SQL du recordset. Si la chaîne ne commence pas par « SELECT » ou « {CALL », l’infrastructure utilise ce qui est fourni pour construire une instance SQL **FROM** clause.

- La chaîne retournée par [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Par défaut, il s’agit du nom de la table que vous avez spécifié pour le jeu d’enregistrements dans l’Assistant, mais vous pouvez modifier ce que la fonction retourne. Le framework appelle `GetDefaultSQL` — si la chaîne ne commence pas par « SELECT » ou « {CALL », il est supposé être un nom de table, qui est utilisé pour construire la chaîne SQL.


- Données membres de champ de recordset, qui doivent être liés à des colonnes spécifiques de la table. Le framework lie les colonnes enregistrement aux adresses de ces membres, leur utilisation de mémoires tampons. Le framework détermine la corrélation des données membres de champ aux colonnes de table à partir de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou les appels de fonction de RFX en bloc dans le jeu d’enregistrements [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) fonction membre.

- Le [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour le jeu d’enregistrements, le cas échéant, contenus dans le [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) membre de données. L’infrastructure utilise la chaîne pour construire une instance SQL **où** clause.

- Le [tri](../../data/odbc/recordset-sorting-records-odbc.md) ordre à respecter pour le jeu d’enregistrements, si un, contenue dans le [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) membre de données. L’infrastructure utilise la chaîne pour construire une instance SQL **ORDER BY** clause.

   > [!TIP]
   > Pour utiliser le code SQL **GROUP BY** clause (et éventuellement le **HAVING** clause), ajoutez les clauses à la fin de la chaîne de filtre.

- Les valeurs de n’importe quel [les membres de données de paramètre](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que vous spécifiez pour la classe. Vous définissez des valeurs de paramètre avant d’appeler `Open` ou `Requery`. L’infrastructure lie les valeurs de paramètre pour « ? » des espaces réservés dans la chaîne SQL. Au moment de la compilation, vous spécifiez la chaîne avec des espaces réservés. Au moment de l’exécution, l’infrastructure complète dans les détails selon les valeurs de paramètre que vous passez.

`Open` construit une instance SQL **sélectionnez** instruction à partir de ces éléments. Consultez [personnalisation de la sélection](#_core_customizing_the_selection) pour plus d’informations sur la façon dont l’infrastructure utilise les ingrédients.

Après la construction de l’instruction, `Open` envoie le code SQL pour le Gestionnaire de pilotes ODBC (et la bibliothèque de curseurs ODBC si elle est en mémoire), qui à son tour transmet le pilote ODBC pour le SGBD spécifique. Le pilote communique avec le SGBD pour effectuer la sélection sur la source de données et extrait le premier enregistrement. L’infrastructure charge l’enregistrement dans les membres de données de champ de l’objet recordset.

Vous pouvez utiliser une combinaison de ces techniques pour ouvrir [tables](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) et pour construire une requête basée sur un [jointure](../../data/odbc/recordset-performing-a-join-odbc.md) de plusieurs tables. Avec une personnalisation supplémentaire, vous pouvez appeler [requêtes prédéfinies](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procédures stockées), sélectionnez les colonnes ne pas connus au moment du design de la table et [lier](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) les champs du recordset ou vous peuvent effectuer la plupart des autres. tâches d’accès aux données. Tâches que vous ne pouvez pas accomplir en personnalisant les jeux d’enregistrements peuvent toujours être accomplies en [appelant des fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) ou directement à l’exécution des instructions SQL avec [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="_core_customizing_the_selection"></a> Personnalisation de la sélection

En plus de fournir un filtre, un ordre de tri ou des paramètres, vous pouvez effectuer les actions suivantes pour personnaliser la sélection du recordset :

- Passer une chaîne SQL personnalisée dans *lpszSQL* lorsque vous appelez [Open](../../mfc/reference/crecordset-class.md#open) pour le jeu d’enregistrements. Tout ce que vous passez dans *lpsqSQL* est prioritaire sur ce que le [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) fonction membre retourne.

   Pour plus d’informations, consultez [SQL : Personnaliser les instruction SQL (ODBC du Recordset)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), qui décrit les types d’instructions SQL (ou d’instructions partielles), vous pouvez passer à `Open` et le rôle de l’infrastructure avec eux.

    > [!NOTE]
    >  Si la chaîne personnalisée que vous transmettez ne commence pas par « SELECT » ou « {CALL », MFC suppose qu’il contient un nom de table. Cela s’applique également à l’élément suivant à puces.

- Modifier la chaîne que l’Assistant écrit dans le jeu d’enregistrements `GetDefaultSQL` fonction membre. Modifier le code de fonction pour modifier ce qu’elle retourne. Par défaut, l’Assistant écrit un `GetDefaultSQL` fonction qui retourne un nom de table unique.

   Vous pouvez avoir `GetDefaultSQL` retourner les éléments que vous pouvez passer dans le *lpszSQL* paramètre `Open`. Si vous ne passez pas une chaîne SQL personnalisée dans *lpszSQL*, l’infrastructure utilise la chaîne qui `GetDefaultSQL` retourne. Au minimum, `GetDefaultSQL` doit retourner un nom de table unique. Mais vous pouvez lui demander de renvoyer plusieurs noms de tables, d’un intégral **sélectionnez** instruction, une application ODBC **appeler** instruction et ainsi de suite. Pour obtenir la liste de ce que vous pouvez passer à *lpszSQL* — ou avez `GetDefaultSQL` retourner — consultez [SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Si vous effectuez une jointure de deux ou plusieurs tables, réécrivez `GetDefaultSQL` pour personnaliser la liste de tables utilisée dans le SQL **FROM** clause. Pour plus d’informations, consultez [jeu d’enregistrements : Création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).


- Lier manuellement les membres de données de champ supplémentaire, par exemple basés sur les informations sur le schéma de votre source de données en cours d’exécution. Vous ajoutez des membres de données de champ à la classe de jeu d’enregistrements, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou d’appels de fonction de RFX en bloc pour qu’ils puissent le [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) fonction membre, et initialisations des membres de données dans le constructeur de classe. Pour plus d’informations, consultez [jeu d’enregistrements : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Substituer des fonctions membres de jeu d’enregistrements, telles que `OnSetOptions`, pour définir les options spécifiques à l’application ou pour remplacer les valeurs par défaut.

Si vous souhaitez baser le jeu d’enregistrements sur une instruction SQL complexe, vous devez utiliser une combinaison de ces techniques de personnalisation. Par exemple, vous pouvez utiliser les clauses SQL et mots clés pas directement pris en charge par les recordsets ou joindre plusieurs tables.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Modification des enregistrements par mise à jour des jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Recordset : Verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)