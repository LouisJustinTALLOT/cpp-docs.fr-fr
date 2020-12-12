---
description: 'En savoir plus sur : SQL : personnalisation de l’instruction SQL du recordset (ODBC)'
title: "SQL : personnalisation de l'instruction SQL du recordset (ODBC)"
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
ms.openlocfilehash: 73765ed66dacbc017cca6236ae5a90388390fa45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278686"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL : personnalisation de l'instruction SQL du recordset (ODBC)

Cette rubrique répond aux questions suivantes :

- Comment l’infrastructure construit une instruction SQL

- Comment substituer l’instruction SQL

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous utilisez les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Moteur de base de données SQL et ANSI SQL » dans l’aide de DAO.

## <a name="sql-statement-construction"></a>Construction d’instructions SQL

Votre jeu d’enregistrements base la sélection des enregistrements principalement sur une instruction SQL **Select** . Quand vous déclarez votre classe à l’aide d’un Assistant, elle écrit une version de substitution de la `GetDefaultSQL` fonction membre qui ressemble à ceci (pour une classe de Recordset appelée `CAuthors` ).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Par défaut, ce remplacement retourne le nom de la table que vous avez spécifié à l’aide de l’Assistant. Dans l’exemple, le nom de la table est « AUTHORs ». Lorsque vous appelez ultérieurement la fonction membre du recordset `Open` , `Open` construit une instruction **Select** finale de la forme :

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

où `table-name` est obtenu en appelant `GetDefaultSQL` et `rfx-field-list` est obtenu à partir des appels de la fonction RFX dans `DoFieldExchange` . C’est ce que vous pouvez obtenir pour une instruction **Select** , sauf si vous la remplacez par une version de remplacement au moment de l’exécution, bien que vous puissiez également modifier l’instruction par défaut avec des paramètres ou un filtre.

> [!NOTE]
> Si vous spécifiez un nom de colonne qui contient (ou peut contenir) des espaces, vous devez placer le nom entre crochets. Par exemple, le nom « First Name » doit être « [First Name] ».

Pour remplacer l’instruction **Select** par défaut, passez une chaîne contenant une instruction **Select** complète lorsque vous appelez `Open` . Au lieu de construire sa propre chaîne par défaut, le recordset utilise la chaîne que vous fournissez. Si votre instruction de remplacement contient une clause **Where** , ne spécifiez pas de filtre dans `m_strFilter` , car vous auriez alors deux instructions de filtre. De même, si votre instruction de remplacement contient une clause **order by** , ne spécifiez pas de tri dans `m_strSort` afin que vous n’ayez pas deux instructions de tri.

> [!NOTE]
> Si vous utilisez des chaînes littérales dans vos filtres (ou d’autres parties de l’instruction SQL), vous devrez peut-être « citer » (entre les délimiteurs spécifiés) ces chaînes avec un préfixe littéral spécifique au SGBD et un ou plusieurs caractères de suffixe littéral.

Vous pouvez également rencontrer des exigences syntaxiques spéciales pour les opérations telles que les jointures externes, en fonction de votre SGBD. Utilisez les fonctions ODBC pour obtenir ces informations à partir de votre pilote pour le SGBD. Par exemple, appelez `::SQLGetTypeInfo` pour un type de données particulier, tel que `SQL_VARCHAR` , pour demander les caractères LITERAL_PREFIX et LITERAL_SUFFIX. Si vous écrivez du code indépendant de la base de données, consultez l' [annexe C : syntaxe SQL](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) dans le [Guide de référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference) pour obtenir des informations détaillées sur la syntaxe.

Un objet recordset construit l’instruction SQL qu’il utilise pour sélectionner des enregistrements, sauf si vous transmettez une instruction SQL personnalisée. Cette opération dépend principalement de la valeur que vous transmettez dans le paramètre *lpszSQL* de la `Open` fonction membre.

La forme générale d’une instruction SQL **Select** est la suivante :

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Pour ajouter le mot clé **distinct** à l’instruction SQL de votre jeu d’enregistrements, vous pouvez incorporer le mot clé dans le premier appel de fonction RFX dans `DoFieldExchange` . Par exemple :

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Utilisez cette technique uniquement avec un jeu d’enregistrements ouvert en lecture seule.

## <a name="overriding-the-sql-statement"></a>Substitution de l’instruction SQL

Le tableau suivant présente les possibilités du paramètre *lpszSQL* à `Open` . Les cas du tableau sont expliqués à la suite du tableau.

**Le paramètre lpszSQL et la chaîne SQL obtenue**

|Cas|Ce que vous transmettez dans lpszSQL|Instruction SELECT qui en résulte|
|----------|------------------------------|------------------------------------|
|1|NULL|**Select** *RFX-Field-List* **from** *table-Name*<br /><br /> `CRecordset::Open` appelle `GetDefaultSQL` pour récupérer le nom de la table. La chaîne résultante est l’un des cas 2 à 5, en fonction de ce qui est `GetDefaultSQL` retourné.|
|2|Un nom de table|**Select** *RFX-Field-List* **from** *table-Name*<br /><br /> La liste de champs est extraite des instructions RFX dans `DoFieldExchange` . Si `m_strFilter` et ne `m_strSort` sont pas vides, ajoute les clauses **Where** et/ou **order by** .|
|1,3 \*|Une instruction **Select** complète, mais sans clause **Where** ou **order by**|Comme passé. Si `m_strFilter` et ne `m_strSort` sont pas vides, ajoute les clauses **Where** et/ou **order by** .|
|4 \*|Une instruction **Select** complète avec une clause **Where** et/ou **order by**|Comme passé. `m_strFilter` et/ou `m_strSort` doivent rester vides, ou deux instructions de filtre et/ou de tri sont produites.|
|5,5 \*|Un appel à une procédure stockée|Comme passé.|

\*`m_nFields`doit être inférieur ou égal au nombre de colonnes spécifié dans l’instruction **Select** . Le type de données de chaque colonne spécifiée dans l’instruction **Select** doit être le même que le type de données de la colonne de sortie RFX correspondante.

### <a name="case-1---lpszsql--null"></a>Cas 1 lpszSQL = NULL

La sélection du recordset dépend de ce qui est `GetDefaultSQL` retourné lors de `CRecordset::Open` son appel. Les cas 2 à 5 décrivent les chaînes possibles.

### <a name="case-2---lpszsql--a-table-name"></a>Cas 2 lpszSQL = un nom de table

Le recordset utilise RFX (Record Field Exchange) pour générer la liste des colonnes à partir des noms de colonnes fournis dans les appels de fonction RFX dans la substitution de la classe Recordset de `DoFieldExchange` . Si vous avez utilisé un Assistant pour déclarer votre classe de Recordset, ce cas a le même résultat que le cas 1 (à condition que vous passiez le même nom de table que celui que vous avez spécifié dans l’Assistant). Si vous n’utilisez pas d’Assistant pour écrire votre classe, le cas 2 est le moyen le plus simple de construire l’instruction SQL.

L’exemple suivant construit une instruction SQL qui sélectionne des enregistrements à partir d’une application de base de données MFC. Lorsque le Framework appelle la `GetDefaultSQL` fonction membre, la fonction retourne le nom de la table, `SECTION` .

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Pour obtenir les noms des colonnes de l’instruction SQL **Select** , le Framework appelle la `DoFieldExchange` fonction membre.

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

Une fois l’exécution terminée, l’instruction SQL se présente comme suit :

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Cas 3 lpszSQL = a SELECT/FROM (instruction)

Vous spécifiez manuellement la liste des colonnes au lieu de vous appuyer sur RFX pour la construire automatiquement. Vous pouvez effectuer cette opération dans les cas suivants :

- Vous souhaitez spécifier le mot clé **distinct** après **Select**.

   Votre liste de colonnes doit correspondre aux noms de colonne et aux types dans le même ordre que celui dans lequel ils sont répertoriés `DoFieldExchange` .

- Vous avez la raison de récupérer manuellement des valeurs de colonne à l’aide de la fonction ODBC `::SQLGetData` au lieu de vous appuyer sur RFX pour lier et récupérer des colonnes pour vous.

   Vous pouvez, par exemple, souhaiter accepter les nouvelles colonnes qu’un client de votre application a ajoutées aux tables de la base de données après la distribution de l’application. Vous devez ajouter ces membres de données de champ supplémentaires, qui n’étaient pas connus au moment où vous avez déclaré la classe à l’aide d’un Assistant.

   Votre liste de colonnes doit correspondre aux noms et aux types des colonnes dans le même ordre que celui dans lequel ils sont répertoriés `DoFieldExchange` , suivis des noms des colonnes liées manuellement. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Vous souhaitez joindre des tables en spécifiant plusieurs tables dans la clause **from** .

   Pour obtenir des informations et un exemple, consultez [Recordset : exécution d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Cas 4 lpszSQL = SELECT/FROM plus WHERE et/ou ORDER BY

Vous spécifiez tout : la liste des colonnes (en fonction des appels RFX dans `DoFieldExchange` ), la liste des tables et le contenu d’une clause **Where** et/ou **order by** . Si vous spécifiez des clauses **Where** et/ou **order by** de cette manière, n’utilisez pas `m_strFilter` et/ou `m_strSort` .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Cas 5 lpszSQL = un appel de procédure stockée

Si vous devez appeler une requête prédéfinie (par exemple, une procédure stockée dans une base de données Microsoft SQL Server), vous devez écrire une instruction **Call** dans la chaîne que vous transmettez à *lpszSQL*. Les assistants ne prennent pas en charge la déclaration d’une classe de Recordset pour l’appel d’une requête prédéfinie. Les requêtes prédéfinies ne retournent pas toutes les enregistrements.

Si une requête prédéfinie ne retourne pas d’enregistrements, vous pouvez utiliser `CDatabase` directement la fonction membre `ExecuteSQL` . Pour une requête prédéfinie qui retourne des enregistrements, vous devez également écrire manuellement les appels RFX dans `DoFieldExchange` pour toutes les colonnes retournées par la procédure. Les appels RFX doivent être dans le même ordre et retourner les mêmes types, comme la requête prédéfinie. Pour plus d’informations, consultez [Recordset : déclaration d’une classe pour une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Voir aussi

[SQL : types de données SQL et C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
