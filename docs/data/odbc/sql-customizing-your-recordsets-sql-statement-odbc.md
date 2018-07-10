---
title: 'SQL : Personnalisation d’instruction SQL de votre jeu d’enregistrements (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f385127d1b61e1453eb7a079963da727f82f1874
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098587"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL : personnalisation de l'instruction SQL du recordset (ODBC)
Cette rubrique explique :  
  
-   Comment l’infrastructure construit une instruction SQL  
  
-   Procédure de remplacement de l’instruction SQL  
  
> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL » dans l’aide de DAO.  
  
## <a name="sql-statement-construction"></a>Construction d’instructions SQL  
 Votre recordset base la sélection des enregistrements principalement sur un SQL **sélectionnez** instruction. Lorsque vous déclarez votre classe avec un Assistant, il écrit une version de substitution de la `GetDefaultSQL` fonction membre qui ressemble à ceci (pour une classe de recordset appelé `CAuthors`).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 Par défaut, cette substitution retourne le nom de table que vous avez spécifié à l’aide de l’Assistant. Dans l’exemple, le nom de table est « Auteurs ». Lorsque vous appelez ultérieurement le jeu d’enregistrements **ouvrir** fonction membre, **ouvrir** construit finale **sélectionnez** instruction du formulaire :  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 où `table-name` est obtenu en appelant `GetDefaultSQL` et `rfx-field-list` est obtenu à partir des appels de fonction RFX dans `DoFieldExchange`. C’est ce que vous obtenez pour un **sélectionnez** instruction, sauf si vous le remplacer par une version de remplacement au moment de l’exécution, bien que vous pouvez également modifier l’instruction par défaut avec des paramètres ou un filtre.  
  
> [!NOTE]
>  Si vous spécifiez un nom de colonne qui contienne (ou peut contenir) des espaces, vous devez placer le nom entre crochets. Par exemple, le nom « Prénom » doit être « [Prénom] ».  
  
 Pour remplacer la valeur par défaut **sélectionnez** instruction, passe une chaîne contenant un **sélectionnez** instruction lorsque vous appelez **ouvrir**. Au lieu de construire sa propre chaîne par défaut, le jeu d’enregistrements utilise la chaîne que vous fournissez. Si l’instruction de remplacement contient un **où** clause, ne spécifiez pas un filtre dans **m_strFilter** , car vous avez alors deux instructions de filtre. De même, si l’instruction de remplacement contient un **ORDER BY** clause, ne spécifiez pas de tri dans `m_strSort` afin que vous n’aurez pas deux instructions de tri.  
  
> [!NOTE]
>  Si vous utilisez des chaînes littérales dans vos filtres (ou d’autres parties de l’instruction SQL), vous devrez peut-être « quote » (placer des délimiteurs spécifiés) suffixe de ces chaînes avec le préfixe littéral propres au SGBD et littéral (ou les caractères).  
  
 Vous pouvez également rencontrer des exigences syntaxiques particulières pour les opérations telles que les jointures externes, en fonction de votre SGBD. Utilisez les fonctions ODBC pour obtenir ces informations à partir de votre pilote du SGBD. Par exemple, appeler **:: SQLGetTypeInfo** pour un type de données particulier, tel que **SQL_VARCHAR**, pour demander le **LITERAL_PREFIX** et **LITERAL_SUFFIX** caractères. Si vous écrivez du code indépendant de la base de données, consultez l’annexe C le *ODBC SDK ** de référence du programmeur* sur le CD-ROM MSDN Library pour les informations de syntaxe détaillées.  
  
 Un objet recordset construit l’instruction SQL qu’il utilise pour sélectionner des enregistrements, sauf si vous passez d’une instruction SQL personnalisée. Cette opération dépend principalement de la valeur que vous passez dans le `lpszSQL` paramètre de la **ouvrir** fonction membre.  
  
 La forme générale d’un service SQL **sélectionnez** instruction est :  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Une façon d’ajouter le **DISTINCT** mot clé à l’instruction SQL du recordset consiste à incorporer le mot clé dans le premier appel de fonction RFX dans `DoFieldExchange`. Par exemple :  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Utilisez cette technique uniquement avec un jeu d’enregistrements ouvert en lecture seule.  
  
## <a name="overriding-the-sql-statement"></a>Substitution de l’instruction SQL  
 Le tableau suivant montre les possibilités de la `lpszSQL` paramètre **ouvrir**. Les cas dans la table sont expliqués le tableau suivant.  
  
 **Le paramètre lpszSQL et la chaîne SQL obtenue**  
  
|Case|Vous passez à lpszSQL|L’instruction SELECT résultante|  
|----------|------------------------------|------------------------------------|  
|1|**NULL**|**Sélectionnez** *liste de champs de rfx* **FROM** *-nom de la table*<br /><br /> `CRecordset::Open` appels `GetDefaultSQL` pour obtenir le nom de la table. La chaîne obtenue est un des cas 2 à 5, selon ce qui `GetDefaultSQL` retourne.|  
|2|Un nom de table|**Sélectionnez** *liste de champs de rfx* **FROM** *-nom de la table*<br /><br /> La liste de champs est extraite des instructions RFX dans `DoFieldExchange`. Si **m_strFilter** et `m_strSort` ne sont pas vides, ajoute le **où** et/ou **ORDER BY** clauses.|  
|3 *|Complète **sélectionnez** instruction mais sans un **où** ou **ORDER BY** clause|Comme réussi. Si **m_strFilter** et `m_strSort` ne sont pas vides, ajoute le **où** et/ou **ORDER BY** clauses.|  
|4 *|Complète **sélectionnez** instruction avec un **où** et/ou **ORDER BY** clause|Comme réussi. **m_strFilter** et/ou `m_strSort` doivent rester vides, ou deux filtre et/ou les instructions de tri sont produites.|  
|5 *|Un appel à une procédure stockée|Comme réussi.|  
  
 \* `m_nFields` doit être inférieur ou égal au nombre de colonnes spécifié dans le **sélectionnez** instruction. Le type de données de chaque colonne spécifiée dans le **sélectionnez** instruction doit être le même que le type de données de la colonne de sortie RFX correspondante.  
  
### <a name="case-1---lpszsql--null"></a>Cas 1 lpszSQL = NULL  
 La sélection du recordset dépend `GetDefaultSQL` retourne lorsque `CRecordset::Open` appelle. Cas 2 à 5 décrivent les chaînes possibles.  
  
### <a name="case-2---lpszsql--a-table-name"></a>Cas 2 lpszSQL = nom de Table  
 Le jeu d’enregistrements utilise l’échange de champs d’enregistrements (RFX) pour générer la liste des colonnes à partir des noms de colonnes fournis dans la fonction appels RFX dans la substitution de la classe du jeu d’enregistrements `DoFieldExchange`. Si vous avez utilisé un Assistant pour déclarer la classe de recordset, cet incident a le même résultat que le cas 1 (à condition que vous passez le même nom de table que vous avez spécifié dans l’Assistant). Si vous n’utilisez pas un Assistant pour écrire votre classe, le cas 2 est le plus simple pour construire l’instruction SQL.  
  
 L’exemple suivant construit une instruction SQL qui sélectionne des enregistrements à partir d’une application de base de données MFC. Lorsque l’infrastructure appelle la `GetDefaultSQL` membre, la fonction retourne le nom de la table, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Pour obtenir les noms des colonnes pour l’instruction SQL **sélectionnez** instruction, le framework appelle la `DoFieldExchange` fonction membre.  
  
```  
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
  
 Lorsque vous avez terminé, l’instruction SQL ressemble à ceci :  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Cas 3 lpszSQL = SELECT / à partir de l’instruction  
 Vous spécifiez la liste des colonnes manuellement au lieu de compter sur RFX pour la construire automatiquement. Vous pouvez souhaiter faire lorsque :  
  
-   Vous souhaitez spécifier le **DISTINCT** suivant de mot clé **sélectionnez**.  
  
     Liste des colonnes doit correspondre aux noms de colonnes et les types dans le même ordre que celui répertorié dans `DoFieldExchange`.  
  
-   Vous devez extraire manuellement les valeurs de colonne à l’aide de la fonction ODBC **:: SQLGetData** plutôt que de laisser RFX lier et récupérer automatiquement les colonnes.  
  
     Vous pourriez par exemple prendre en compte les nouvelles colonnes, qu'un client de votre application sont ajouté aux tables de base de données une fois que l’application a été distribuée. Vous devez ajouter ces membres de données de champ supplémentaire, qui n’étaient pas connus au moment de la que déclaration de la classe avec un Assistant.  
  
     Liste des colonnes doit correspondre aux noms de colonnes et les types dans le même ordre que celui répertorié dans `DoFieldExchange`, suivie des noms de colonnes liées manuellement. Pour plus d’informations, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Vous voulez joindre des tables en spécifiant plusieurs tables dans le **FROM** clause.  
  
     Pour plus d’informations et obtenir un exemple, consultez [Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Cas 4 lpszSQL = SELECT / à partir de Plus où et/ou ORDER BY  
 Vous fournissez toutes les informations : la liste des colonnes (basé sur les appels RFX `DoFieldExchange`), la liste de tables et le contenu d’un **où** et/ou un **ORDER BY** clause. Si vous spécifiez votre **où** et/ou **ORDER BY** clauses de cette manière, n’utilisez pas **m_strFilter** et/ou `m_strSort`.  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Cas 5 lpszSQL = un appel de procédure stockée  
 Si vous avez besoin d’appeler une requête prédéfinie (par exemple, une procédure stockée dans une base de données Microsoft SQL Server), vous devez écrire un **appeler** instruction dans la chaîne que vous passez à `lpszSQL`. Les Assistants ne gèrent pas la déclaration de la classe de recordset pour l’appel d’une requête prédéfinie. Toutes les requêtes prédéfinies retournent des enregistrements.  
  
 Si une requête prédéfinie ne retourne pas d’enregistrements, vous pouvez utiliser la `CDatabase` fonction membre `ExecuteSQL` directement. Pour une requête prédéfinie qui retourne des enregistrements, vous devez également écrire manuellement les appels RFX dans `DoFieldExchange` pour toutes les colonnes, la procédure retourne. Les appels RFX doivent être dans le même ordre et retourner les mêmes types, comme la requête prédéfinie. Pour plus d’informations, consultez [Recordset : déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL : SQL et Types de données C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
