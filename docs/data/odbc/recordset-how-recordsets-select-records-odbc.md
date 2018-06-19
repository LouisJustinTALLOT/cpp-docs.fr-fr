---
title: 'Recordset : Comment Recordsets sélection d’enregistrements (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9ff2f1e9946eb32356eb09fa2ee216aa636a351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093228"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Recordset : sélection d'enregistrements par les recordsets (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique :  
  
-   [Votre rôle et options de sélection des enregistrements](#_core_your_options_in_selecting_records).  
  
-   [Comment un recordset construit son instruction SQL et sélectionne les enregistrements](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Ce que vous pouvez faire pour personnaliser la sélection](#_core_customizing_the_selection).  
  
 Jeux d’enregistrements de sélectionner des enregistrements à partir d’une source de données via un pilote ODBC en envoyant des instructions SQL au pilote. L’instruction SQL envoyée dépend de votre conception et ouvrez votre classe de recordset.  
  
##  <a name="_core_your_options_in_selecting_records"></a> Vos Options de sélection des enregistrements  
 Le tableau suivant répertorie les options de sélection des enregistrements.  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>Quand et comment vous pouvez affecter un jeu d’enregistrements  
  
|Lorsque vous|Vous pouvez|  
|--------------|-------------|  
|Déclarez votre classe de jeu d’enregistrements avec les **ajouter une classe** Assistant|Spécifier la table pour sélectionner à partir de.<br /><br /> Spécifiez les colonnes à inclure.<br /><br /> Consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Terminer votre implémentation de la classe de recordset|Substituer des fonctions membres telles que `OnSetOptions` (Avancé) pour définir des options spécifiques à l’application ou pour modifier les valeurs par défaut. Définir les membres de données de paramètre si vous voulez un recordset paramétré.|  
|Construisez un objet recordset (avant d’appeler **ouvrir**)|Spécifiez une condition de recherche (éventuellement composée) à utiliser dans un **où** clause qui filtre les enregistrements. Consultez [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Spécifier un ordre de tri pour une utilisation dans un **ORDER BY** clause qui trie les enregistrements. Consultez [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Spécifiez les valeurs de paramètre pour tous les paramètres que vous avez ajouté à la classe. Consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  

| Exécuter la requête du recordset en appelant **ouvrir**| Spécifiez une chaîne SQL personnalisée pour remplacer la chaîne SQL par défaut configurée par l’Assistant. Consultez [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) dans les *référence de bibliothèque de classe* et [SQL : personnalisation de l’instruction SQL du Recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |  

| Appelez **Requery** pour actualiser le jeu d’enregistrements avec les valeurs les plus récentes sur la source de données | Spécifiez les nouveaux paramètres, filtrer ou trier. Consultez [Recordset : actualisation d’un jeu d’enregistrements (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Comment un Recordset construit son instruction SQL  
 Lorsque vous appelez l’objet recordset [ouvrir](../../mfc/reference/crecordset-class.md#open) fonction membre, **ouvrir** construit une instruction SQL à l’aide de tout ou partie des éléments suivants :  
  
-   Le **lpszSQL** paramètre passé à **ouvrir**. Si ce n’est pas **NULL**, ce paramètre spécifie une chaîne SQL personnalisée ou une partie d’un. La structure analyse la chaîne. Si la chaîne SQL **sélectionnez** instruction ou une application ODBC **appeler** instruction, le framework utilise la chaîne comme instruction SQL du recordset. Si la chaîne ne commence pas par « SELECT » ou « {CALL », l’infrastructure utilise ce qui est fourni pour construire SQL **FROM** clause.  
  
-   La chaîne retournée par [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Par défaut, il s’agit du nom de la table que vous avez spécifié pour le jeu d’enregistrements dans l’Assistant, mais vous pouvez modifier ce que la fonction retourne. Le framework appelle `GetDefaultSQL` — si la chaîne ne commence pas par « SELECT » ou « {CALL », il est supposé être un nom de table, qui est utilisé pour construire la chaîne SQL.  
  

-   Données membres de champ de recordset, qui doivent être liés à des colonnes spécifiques de la table. L’infrastructure lie les colonnes enregistrement aux adresses de ces membres, les utilisant comme tampons. L’infrastructure détermine la corrélation des données membres de champ aux colonnes de table à partir de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou les appels de fonction de RFX en bloc dans le jeu d’enregistrements [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) fonction membre.  
  
-   Le [filtre](../../data/odbc/recordset-filtering-records-odbc.md) pour le jeu d’enregistrements, le cas échéant, contenus dans le [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) membre de données. L’infrastructure utilise la chaîne pour construire une SQL **où** clause.  
  
-   Le [tri](../../data/odbc/recordset-sorting-records-odbc.md) de commande pour l’ensemble d’enregistrements, si elle existe, contenue dans le [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) membre de données. L’infrastructure utilise la chaîne pour construire une SQL **ORDER BY** clause.  

  
    > [!TIP]
    >  Pour utiliser l’instruction SQL **GROUP BY** clause (et éventuellement le **HAVING** clause), ajoutez les clauses à la fin de la chaîne de filtre.  
  
-   Les valeurs de n’importe quel [les membres de données de paramètre](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) vous spécifiez pour la classe. Vous définissez des valeurs de paramètre avant d’appeler **ouvrir** ou **Requery**. L’infrastructure lie les valeurs de paramètre pour « ? » des espaces réservés dans la chaîne SQL. Au moment de la compilation, vous spécifiez la chaîne avec des espaces réservés. Au moment de l’exécution, l’infrastructure complète les informations selon les valeurs de paramètre que vous passez.  
  
 **Ouvrez** construit SQL **sélectionnez** instruction à partir de ces éléments. Consultez [personnalisation de la sélection](#_core_customizing_the_selection) pour plus d’informations sur la façon dont l’infrastructure utilise les ingrédients.  
  
 Après la construction de l’instruction, **ouvrir** envoie au Gestionnaire de pilotes ODBC (et la bibliothèque de curseurs ODBC si elle est en mémoire), qui à son tour transmet le pilote ODBC du SGBD concerné. Le pilote communique avec le SGBD pour effectuer la sélection sur la source de données et extrait le premier enregistrement. L’infrastructure charge l’enregistrement dans les membres de données de champ de l’objet recordset.  
  
 Vous pouvez utiliser une combinaison de ces techniques pour ouvrir [tables](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) et pour construire une requête basée sur un [jointure](../../data/odbc/recordset-performing-a-join-odbc.md) de plusieurs tables. Avec une personnalisation supplémentaire, vous pouvez appeler [requêtes prédéfinies](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procédures stockées), sélectionnez les colonnes ne pas connus au moment du design de la table et [lier](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) les champs du recordset, ou vous peuvent effectuer la plupart des autres tâches d’accès aux données. Tâches que vous ne pouvez pas effectuer en personnalisant les recordsets peuvent toujours être accomplies en [appel de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) ou directement en exécutant les instructions SQL avec [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
##  <a name="_core_customizing_the_selection"></a> Personnalisation de la sélection  
 En plus de fournir un filtre, un ordre de tri ou des paramètres, vous pouvez effectuer les actions suivantes pour personnaliser la sélection du recordset :  
  
-   Passer une chaîne SQL personnalisée dans **lpszSQL** lorsque vous appelez [ouvrir](../../mfc/reference/crecordset-class.md#open) pour l’ensemble d’enregistrements. Tout ce que vous passez dans **lpsqSQL** est prioritaire sur ce que le [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) fonction membre retourne.  
  
     Pour plus d’informations, consultez [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), qui décrit les types d’instructions SQL (ou d’instructions partielles) que vous pouvez passer à **ouvrir** et ce que le framework fait avec eux.  
  
    > [!NOTE]
    >  Si la chaîne personnalisée que vous passez ne commence pas par « SELECT » ou « {CALL », MFC suppose qu’il contient un nom de table. Cela s’applique également à l’élément de liste à puces suivant.  
  
-   Modifier la chaîne que l’Assistant écrit dans le jeu d’enregistrements `GetDefaultSQL` fonction membre. Modifier le code de fonction pour changer sa valeur de retour. Par défaut, l’Assistant écrit un `GetDefaultSQL` fonction qui retourne un nom de table.  
  
     Vous pouvez avoir `GetDefaultSQL` retourner les éléments que vous pouvez passer dans le **lpszSQL** paramètre **ouvrir**. Si vous ne transmettez pas une chaîne SQL personnalisée dans **lpszSQL**, l’infrastructure utilise la chaîne qui `GetDefaultSQL` retourne. Au minimum, `GetDefaultSQL` doit retourner un nom de table. Mais vous pouvez les renvoyer plusieurs noms de table complète **sélectionnez** instruction, une application ODBC **appeler** instruction et ainsi de suite. Pour obtenir la liste de ce que vous pouvez passer à **lpszSQL** — ou `GetDefaultSQL` retourner — consultez [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
     Si vous effectuez une jointure de deux ou plusieurs tables, réécrivez `GetDefaultSQL` pour personnaliser la liste de table utilisée dans l’instruction SQL **FROM** clause. Pour plus d’informations, consultez [Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  

-   Lier manuellement les membres de données de champ supplémentaires, par exemple basés sur les informations sur le schéma de votre source de données en cours d’exécution. Vous ajoutez des membres de données de champ à la classe de recordset, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ou les appels de fonction de RFX en bloc pour qu’ils le [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) fonction membre, et initialisations des membres de données dans le constructeur de classe. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Substituer des fonctions membres de jeu d’enregistrements, telles que `OnSetOptions`, pour définir des options spécifiques à l’application ou pour remplacer les valeurs par défaut.  
  
 Si vous souhaitez baser le jeu d’enregistrements dans une instruction SQL complexe, vous devez utiliser une combinaison de ces techniques de personnalisation. Par exemple, vous pouvez utiliser les clauses SQL et mots clés pas directement pris en charge par les recordsets ou joindre plusieurs tables.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Modification des jeux d’enregistrements enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Principes de base ODBC](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)