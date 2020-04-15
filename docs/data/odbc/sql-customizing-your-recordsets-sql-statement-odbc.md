---
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
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374515"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL : personnalisation de l'instruction SQL du recordset (ODBC)

Cette rubrique répond aux questions suivantes :

- Comment le cadre construit une déclaration SQL

- Comment remplacer la déclaration SQL

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes MFC DAO, consultez le thème "Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL" dans DAO Help.

## <a name="sql-statement-construction"></a>Construction de déclaration SQL

Votre dossier base la sélection des enregistrements principalement sur une déclaration **SQL SELECT.** Lorsque vous déclarez votre classe avec un assistant, `GetDefaultSQL` il écrit une version prépondérer de `CAuthors`la fonction membre qui ressemble à ceci (pour une classe recordet appelé ).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Par défaut, ce remplacement renvoie le nom de table que vous avez spécifié avec l’assistant. Dans l’exemple, le nom de table est « AUTHORS ». Lorsque vous appelez plus tard `Open` la `Open` fonction membre du recordet, construit une déclaration **SELECT** finale du formulaire :

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

`table-name` où est obtenu `GetDefaultSQL` `rfx-field-list` en appelant et est obtenu à `DoFieldExchange`partir de la fonction RFX appelle en . C’est ce que vous obtenez pour une déclaration **SELECT** sauf si vous la remplacez par une version prépondérer au moment de l’exécution, bien que vous puissiez également modifier l’énoncé par défaut avec des paramètres ou un filtre.

> [!NOTE]
> Si vous spécifiez un nom de colonne qui contient (ou pourrait contenir) des espaces, vous devez enfermer le nom dans des supports carrés. Par exemple, le nom « Prénom » doit être « [prénom]».

Pour remplacer la déclaration **SELECT** par défaut, passez une chaîne `Open`contenant une déclaration **SELECT** complète lorsque vous appelez . Au lieu de construire sa propre chaîne par défaut, le recordet utilise la chaîne que vous fournissez. Si votre relevé de remplacement contient une clause `m_strFilter` **WHERE,** ne spécifiez pas un filtre parce que vous auriez alors deux relevés de filtre. De même, si votre relevé de remplacement contient une `m_strSort` clause **ORDER BY,** ne spécifiez pas une sorte de sorte que vous n’aurez pas deux instructions de tri.

> [!NOTE]
> Si vous utilisez des chaînes littérales dans vos filtres (ou d’autres parties de la déclaration SQL), vous pourriez avoir à «citer» (enclos dans des délimitations spécifiées) de telles chaînes avec un préfixe littéral DBMS et le caractère suffixe littéral (ou des caractères).

Vous pourriez également rencontrer des exigences syntaxes spéciales pour des opérations telles que les jointures extérieures, en fonction de votre DBMS. Utilisez les fonctions ODBC pour obtenir ces informations auprès de votre chauffeur pour le DBMS. Par exemple, `::SQLGetTypeInfo` appelez un type de `SQL_VARCHAR`données particulier, tel que , pour demander les caractères LITERAL_PREFIX et LITERAL_SUFFIX. Si vous écrivez un code indépendant dans la base de données, consultez [l’annexe C: SQL Grammar](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) dans la [référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference) pour des informations détaillées sur la syntaxe.

Un objet de recordet construit la déclaration SQL qu’il utilise pour sélectionner des enregistrements à moins que vous passiez une déclaration SQL personnalisée. La façon dont cela est fait dépend principalement de la valeur que `Open` vous passez dans le paramètre *lpszSQL* de la fonction membre.

La forme générale d’une déclaration **SQL SELECT** est la suivante :

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Une façon d’ajouter le mot clé **DISTINCT** à la déclaration SQL de votre dossier `DoFieldExchange`est d’intégrer le mot clé dans le premier appel de fonction RFX . Par exemple :

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Utilisez cette technique uniquement avec un livre ouvert uniquement comme lu.

## <a name="overriding-the-sql-statement"></a>L’emporter sur la déclaration sqL

Le tableau suivant montre les possibilités pour le paramètre *lpssSQL* à `Open`. Les cas dans le tableau sont expliqués en suivant le tableau.

**Le paramètre lpszSQL et la chaîne SQL résultant**

|Cas|Ce que vous passez en lpszSQL|La déclaration SELECT qui en résulte|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> `CRecordset::Open`appels `GetDefaultSQL` pour obtenir le nom de table. La chaîne résultante est l’un des cas `GetDefaultSQL` 2 à 5, selon les retours.|
|2|Un nom de table|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> La liste de terrain est tirée `DoFieldExchange`des relevés RFX en . Si `m_strFilter` `m_strSort` et ne sont pas vides, ajoute les clauses **WHERE** et/ou **ORDER BY.**|
|3\*|Une déclaration **SELECT** complète mais sans clause **WHERE** ou **ORDER BY**|Comme passé. Si `m_strFilter` `m_strSort` et ne sont pas vides, ajoute les clauses **WHERE** et/ou **ORDER BY.**|
|4\*|Une déclaration **SELECT** complète avec une clause **WHERE** et/ou **ORDER BY**|Comme passé. `m_strFilter`et/ou `m_strSort` doivent rester vides, ou deux relevés de filtre et/ou de tri sont produits.|
|5\*|Un appel à une procédure stockée|Comme passé.|

\*`m_nFields` doivent être inférieurs ou égaux au nombre de colonnes spécifiées dans l’instruction **SELECT.** Le type de données de chaque colonne spécifiée dans l’instruction **SELECT** doit être le même que le type de données de la colonne de sortie RFX correspondante.

### <a name="case-1---lpszsql--null"></a>Cas 1 lpszSQL - NULL

La sélection des enregistrements `GetDefaultSQL` dépend `CRecordset::Open` de ce qui revient lorsque l’appelle. Les cas 2 à 5 décrivent les cordes possibles.

### <a name="case-2---lpszsql--a-table-name"></a>Cas 2 lpszSQL - un nom de table

Le recordet utilise l’échange de champ record (RFX) pour construire la liste de colonne à partir `DoFieldExchange`des noms de colonnes fournis dans les appels de fonction RFX dans la override de la classe de l’enregistrement de . Si vous avez utilisé un assistant pour déclarer votre classe de recordet, ce cas a le même résultat que le cas 1 (à condition que vous passiez le même nom de table que vous avez spécifié dans l’assistant). Si vous n’utilisez pas un assistant pour écrire votre classe, le cas 2 est le moyen le plus simple de construire la déclaration SQL.

L’exemple suivant construit un relevé SQL qui sélectionne les enregistrements d’une application de base de données MFC. Lorsque le cadre `GetDefaultSQL` appelle la fonction membre, la `SECTION`fonction renvoie le nom de la table, .

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Pour obtenir les noms des colonnes pour la déclaration `DoFieldExchange` **SQL SELECT,** le cadre appelle la fonction membre.

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

Une fois terminé, la déclaration SQL ressemble à ceci:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Cas 3 lpszSQL - une déclaration SELECT/FROM

Vous spécifiez la liste de colonnes à la main plutôt que de compter sur RFX pour la construire automatiquement. Vous voudrez peut-être le faire lorsque :

- Vous souhaitez spécifier le mot clé **DISTINCT** suivant **SELECT**.

   Votre liste de colonnes doit correspondre aux noms et `DoFieldExchange`types de colonnes dans le même ordre qu’ils sont répertoriés dans .

- Vous avez des raisons de récupérer manuellement `::SQLGetData` les valeurs de colonnes à l’aide de la fonction ODBC plutôt que de compter sur RFX pour lier et récupérer des colonnes pour vous.

   Vous pouvez, par exemple, accueillir de nouvelles colonnes d’un client de votre application ajouté aux tables de base de données après la distribution de l’application. Vous devez ajouter ces membres de données de terrain supplémentaires, qui n’étaient pas connus au moment où vous avez déclaré la classe avec un assistant.

   Votre liste de colonnes doit correspondre aux noms et `DoFieldExchange`types de colonnes dans le même ordre qu’ils sont répertoriés dans , suivi par les noms des colonnes manuellement liées. Pour plus d’informations, voir [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Vous souhaitez rejoindre les tables en spécifiant plusieurs tables de la clause **FROM.**

   Pour plus d’informations et un exemple, voir [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Cas 4 lpszSQL - SELECT/FROM Plus Où et/ou ORDER BY

Vous spécifiez tout : la liste `DoFieldExchange`de colonnes (basée sur les appels RFX), la liste de table, et le contenu d’une clause **WHERE** et/ou un **ORDER BY.** Si vous spécifiez vos clauses **WHERE** et/ou `m_strSort`ORDER **BY** de cette façon, n’utilisez `m_strFilter` pas et/ou .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Cas 5 lpszSQL - un appel de procédure stocké

Si vous avez besoin d’appeler une requête prédéfinie (comme une procédure stockée dans une base de données Microsoft SQL Server), vous devez écrire une déclaration **CALL** dans la chaîne que vous passez à *lpszSQL*. Les sorciers ne sont pas en faveur de déclarer une classe recordet pour appeler une requête prédéfinie. Toutes les requêtes prédéfinies ne renvoient pas les dossiers.

Si une requête prédéfinie ne renvoie pas `CDatabase` d’enregistrements, vous pouvez utiliser la fonction `ExecuteSQL` du membre directement. Pour une requête prédéfinie qui renvoie les enregistrements, vous devez `DoFieldExchange` également écrire manuellement les appels RFX pour toutes les colonnes de la procédure retourne. Les appels RFX doivent être dans le même ordre et retourner les mêmes types, que la requête prédéfinie. Pour plus d’informations, voir [Recordset: Déclarer une classe pour une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Voir aussi

[SQL : types de données SQL et C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
