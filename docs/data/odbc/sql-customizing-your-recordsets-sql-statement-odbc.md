---
title: 'SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: eabaab019ee94b0c5617573c534d920ec710e9b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329931"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)

Cette rubrique explique :

- Comment l’infrastructure construit une instruction SQL

- Procédure de remplacement de l’instruction SQL

> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL » dans l’aide de DAO.

## <a name="sql-statement-construction"></a>Construction d’instructions SQL

Votre jeu d’enregistrements base la sélection des enregistrement principalement sur un SQL **sélectionnez** instruction. Lorsque vous déclarez votre classe avec un Assistant, il écrit une version de remplacement de la `GetDefaultSQL` fonction membre qui ressemble à ceci (pour une classe de jeu d’enregistrements appelé `CAuthors`).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Par défaut, cette substitution retourne le nom de table que vous avez spécifié avec l’Assistant. Dans l’exemple, le nom de table est « Auteurs ». Lorsque vous appelez ultérieurement le jeu d’enregistrements `Open` fonction membre, `Open` construit une dernière **sélectionnez** instruction du formulaire :

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

où `table-name` est obtenu en appelant `GetDefaultSQL` et `rfx-field-list` est obtenue à partir des appels de fonction RFX dans `DoFieldExchange`. C’est ce que vous obtenez pour un **sélectionnez** instruction, sauf si vous le remplacer par une version de remplacement en cours d’exécution, bien que vous pouvez également modifier l’instruction par défaut avec des paramètres ou un filtre.

> [!NOTE]
>  Si vous spécifiez un nom de colonne qui contienne (ou peut contenir) des espaces, vous devez placer le nom entre crochets. Par exemple, le nom « First Name » doit être « [Prénom] ».

Pour remplacer la valeur par défaut **sélectionnez** instruction, passe une chaîne contenant une liste complète **sélectionnez** instruction lorsque vous appelez `Open`. Au lieu de construire sa propre chaîne par défaut, le jeu d’enregistrements utilise la chaîne que vous fournissez. Si l’instruction de remplacement contient un **où** clause, ne spécifiez pas un filtre dans `m_strFilter` , car vous avez alors deux instructions de filtre. De même, si l’instruction de remplacement contient un **ORDER BY** clause, ne spécifiez pas un tri dans `m_strSort` afin que vous n’avez pas deux instructions de tri.

> [!NOTE]
>  Si vous utilisez des chaînes littérales dans vos filtres (ou d’autres parties de l’instruction SQL), vous devrez peut-être « quote » (entourez de délimiteurs spécifiés) ces chaînes avec un préfixe littéral propres au SGBD et littéral suffixe (ou les caractères).

Vous pouvez également rencontrer des exigences syntaxiques particulières pour les opérations telles que les jointures externes, en fonction de votre SGBD. Utilisez les fonctions ODBC pour obtenir ces informations à partir de votre pilote pour le SGBD. Par exemple, appeler `::SQLGetTypeInfo` pour un type de données particulier, tel que `SQL_VARCHAR`, afin d’obtenir les caractères LITERAL_PREFIX et LITERAL_SUFFIX. Si vous écrivez du code indépendant de la base de données, consultez [annexe c : Grammaire SQL](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) dans le [de référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference) pour des informations sur la syntaxe détaillée.

Un objet recordset construit l’instruction SQL qu’il utilise pour sélectionner des enregistrements, sauf si vous passez d’une instruction SQL personnalisée. Cette opération dépend principalement de la valeur que vous passez dans le *lpszSQL* paramètre de la `Open` fonction membre.

La forme générale d’une instance SQL **sélectionnez** instruction est :

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Une façon d’ajouter le **DISTINCT** mot clé à l’instruction SQL du recordset consiste à incorporer le mot clé dans le premier appel de fonction RFX dans `DoFieldExchange`. Exemple :

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
>  Utilisez cette technique uniquement avec un jeu d’enregistrements ouvert en lecture seule.

## <a name="overriding-the-sql-statement"></a>Substitution de l’instruction SQL

Le tableau suivant présente les possibilités de la *lpszSQL* paramètre `Open`. Les cas dans la table sont expliquées le tableau suivant.

**Le paramètre lpszSQL et la chaîne SQL obtenue**

|Case|Vous transmettez dans lpszSQL|L’instruction SELECT résultante|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> `CRecordset::Open` appels `GetDefaultSQL` pour obtenir le nom de table. La chaîne obtenue est un des cas 2 à 5, selon ce que `GetDefaultSQL` retourne.|
|2|Un nom de table|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> La liste de champs est extraite des instructions RFX dans `DoFieldExchange`. Si `m_strFilter` et `m_strSort` ne sont pas vides, ajoute le **où** et/ou **ORDER BY** clauses.|
|3 \*|Complète **sélectionnez** instruction mais sans un **où** ou **ORDER BY** clause|En tant que réussite. Si `m_strFilter` et `m_strSort` ne sont pas vides, ajoute le **où** et/ou **ORDER BY** clauses.|
|4 \*|Complète **sélectionnez** instruction avec un **où** et/ou **ORDER BY** clause|En tant que réussite. `m_strFilter` et/ou `m_strSort` doivent rester vides, ou deux filtre et/ou d’instructions de tri sont produites.|
|5 \*|Un appel à une procédure stockée|En tant que réussite.|

\* `m_nFields` doit être inférieur ou égal au nombre de colonnes spécifié dans le **sélectionnez** instruction. Le type de données de chaque colonne spécifiée dans le **sélectionnez** instruction doit être le même que le type de données de la colonne de sortie RFX correspondante.

### <a name="case-1---lpszsql--null"></a>Case 1   lpszSQL = NULL

La sélection du recordset dépend `GetDefaultSQL` retourne lorsque `CRecordset::Open` appelle. Cas 2 à 5 décrivent les chaînes possibles.

### <a name="case-2---lpszsql--a-table-name"></a>Cas 2 lpszSQL = nom de Table

Le jeu d’enregistrements utilise des record field exchange (RFX) pour générer la liste des colonnes à partir des noms de colonnes fournis dans la fonction appels RFX dans la substitution de la classe de jeu d’enregistrements de `DoFieldExchange`. Si vous avez utilisé un Assistant pour déclarer votre classe de jeu d’enregistrements, ce cas a le même résultat que le cas 1 (à condition que vous passez le même nom de table que vous avez spécifié dans l’Assistant). Si vous n’utilisez pas un Assistant pour écrire votre classe, le cas 2 est le moyen le plus simple pour construire l’instruction SQL.

L’exemple suivant construit une instruction SQL qui sélectionne des enregistrements à partir d’une application de base de données MFC. Lorsque l’infrastructure appelle la `GetDefaultSQL` fonction membre, la fonction retourne le nom de la table, `SECTION`.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Pour obtenir les noms des colonnes pour le SQL **sélectionnez** instruction, le framework appelle la `DoFieldExchange` fonction membre.

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Lorsque vous avez terminé, l’instruction SQL se présente comme suit :

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Cas 3 lpszSQL = une instruction SELECT ou à partir de l’instruction

Vous spécifiez la liste des colonnes manuellement plutôt que d’utiliser RFX pour la construire automatiquement. Vous souhaiterez peut-être le faire quand :

- Vous souhaitez spécifier le **DISTINCT** suivante de mot clé **sélectionnez**.

   Liste des colonnes doit correspondre les noms de colonnes et les types dans le même ordre qu’ils sont répertoriés dans `DoFieldExchange`.

- Vous avez raison de récupérer manuellement les valeurs de colonne à l’aide de la fonction ODBC `::SQLGetData` plutôt que d’utiliser RFX lier et récupérer automatiquement les colonnes.

   Peut, par exemple, voulez-vous prendre en charge de nouvelles colonnes, qu'un client de votre application est ajouté à la base de données une fois que l’application a été distribuée. Vous devez ajouter ces membres de données de champ supplémentaire, ont été pas connus au moment où que vous avez déclaré la classe avec un Assistant.

   Liste des colonnes doit correspondre les noms de colonnes et les types dans le même ordre qu’ils sont répertoriés dans `DoFieldExchange`, suivie des noms de colonnes liées manuellement. Pour plus d’informations, consultez [jeu d’enregistrements : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Vous souhaitez joindre des tables en spécifiant plusieurs tables dans le **FROM** clause.

   Pour plus d’informations et un exemple, consultez [jeu d’enregistrements : Création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Cas 4 lpszSQL = SELECT / à partir de Plus où et/ou ORDER BY

Vous spécifiez tous les éléments : la liste des colonnes (basé sur les appels RFX dans `DoFieldExchange`), la liste de tables et le contenu d’un **où** et/ou un **ORDER BY** clause. Si vous spécifiez votre **où** et/ou **ORDER BY** clauses de cette façon, n’utilisez pas `m_strFilter` et/ou `m_strSort`.

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Cas 5 lpszSQL = un appel de procédure stockée

Si vous avez besoin d’appeler une requête prédéfinie (par exemple, une procédure stockée dans une base de données Microsoft SQL Server), vous devez écrire un **appeler** instruction dans la chaîne que vous transmettez à *lpszSQL*. Les Assistants ne prennent pas en charge la déclarer une classe de recordset pour l’appel d’une requête prédéfinie. Toutes les requêtes prédéfinies renvoient des enregistrements.

Si une requête prédéfinie ne retourne pas d’enregistrements, vous pouvez utiliser la `CDatabase` fonction membre `ExecuteSQL` directement. Pour une requête prédéfinie qui retourne des enregistrements, vous devez également écrire manuellement les appels RFX dans `DoFieldExchange` pour toutes les colonnes, la procédure retourne. Les appels RFX doivent être dans le même ordre et retourner les mêmes types, que la requête prédéfinie. Pour plus d’informations, consultez [jeu d’enregistrements : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Voir aussi

[SQL : Types de données SQL et C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL : Appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
