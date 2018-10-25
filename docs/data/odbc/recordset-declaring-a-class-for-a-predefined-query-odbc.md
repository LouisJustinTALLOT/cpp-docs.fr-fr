---
title: 'Recordset : Déclaration de la classe d’une requête prédéfinie (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 187b24b45ca24d45f6dd0f3f38cf62120633c790
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071243"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Recordset : déclaration de la classe d'une requête prédéfinie (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment créer une classe de recordset pour une requête prédéfinie (parfois appelée une procédure stockée, comme dans Microsoft SQL Server).

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si l’extraction de lignes en bloc est implémentée, le processus est très similaire. Pour comprendre les différences entre les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc et ceux qui ne le faites pas, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Certains systèmes de gestion de base de données (SGBD) permettent de créer une requête prédéfinie et appelez-la à partir de votre programme comme une fonction. La requête a un nom, peut prendre des paramètres et peut retourner des enregistrements. La procédure décrite dans cette rubrique décrit comment appeler une requête prédéfinie qui retourne des enregistrements (et accepte des paramètres).

Les classes de base de données ne prennent pas en charge la mise à jour des requêtes prédéfinies. La différence entre une requête prédéfinie instantané et une requête prédéfinie feuille de réponse dynamique n’est pas mise à jour, mais si les modifications apportées par d’autres utilisateurs (ou d’autres jeux d’enregistrements dans votre programme) sont visibles dans le jeu d’enregistrements.

> [!TIP]
>  Vous n’avez pas besoin d’un jeu d’enregistrements pour appeler une requête prédéfinie qui ne retourne pas d’enregistrements. Préparer l’instruction SQL comme décrit ci-dessous, mais exécutez-la en appelant le `CDatabase` fonction membre [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Vous pouvez créer une seule classe de recordset pour gérer l’appel d’une requête prédéfinie, mais vous devez faire partie du travail par vous-même. Les Assistants ne prennent pas en charge la création d’une classe spécialement à cet effet.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Pour créer une classe pour l’appel d’une requête prédéfinie (procédure stockée)

1. Utilisez le [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **ajouter une classe** pour créer une classe de jeu d’enregistrements pour la table qui contribue le plus les colonnes retournées par la requête. Cela vous donne un point de départ.

1. Ajoutez manuellement les membres de données de champ pour toutes les colonnes de toutes les tables retournées par la requête mais que l’Assistant n’a pas été créé pour vous.

   Par exemple, si la requête retourne trois colonnes de deux tables supplémentaires, ajoutez six membres de données de champ (les types de données appropriés) à la classe.

1. Ajouter manuellement des [RFX](../../data/odbc/record-field-exchange-rfx.md) appels de fonction dans le [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) fonction membre de la classe, un correspondant au type de données de chaque ajouté des membres de données de champ.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Vous devez connaître les types de données et l’ordre des colonnes retournées dans le résultat défini. L’ordre de la fonction RFX appelle `DoFieldExchange` doit correspondre à l’ordre des colonnes de jeu de résultats.

1. Ajoutez manuellement les initialisations pour les nouveaux membres de données de champ dans le constructeur de classe de jeu d’enregistrements.

   Vous devez également incrémenter la valeur d’initialisation pour le [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) membre de données. L’Assistant écrit l’initialisation, mais elle couvre uniquement les données membres de champ qu’il ajoute automatiquement. Exemple :

    ```cpp
    m_nFields += 6;
    ```

   Certains types de données ne doivent pas être initialisés ici, par exemple, `CLongBinary` ou des tableaux d’octets.

1. Si la requête accepte des paramètres, ajoutez un membre de données de paramètre pour chaque paramètre, un appel de fonctions RFX et une initialisation pour chacun.

1. Vous devez incrémenter `m_nParams` pour chaque paramètre ajouté, comme vous le faisiez `m_nFields` pour les champs ajoutés à l’étape 4 de cette procédure. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Écrire manuellement une chaîne d’instruction SQL avec la forme suivante :

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   où **appeler** est un mot clé ODBC, **nom de la procédure** est le nom de la requête tel qu’il est connu sur la source de données et le « ? » éléments sont des espaces réservés pour les valeurs de paramètre que vous fournissez pour le jeu d’enregistrements en cours d’exécution (le cas échéant) . L’exemple suivant prépare un espace réservé pour un seul paramètre :

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. Dans le code qui ouvre le recordset, définissez les valeurs du paramètre de jeu d’enregistrements de membres de données, puis appelez le `Open` fonction membre, en passant votre chaîne SQL pour le *lpszSQL* paramètre. Ou au lieu de cela, remplacez la chaîne retournée par la `GetDefaultSQL` fonction membre dans votre classe.

Les exemples suivants montrent la procédure d’appel d’une requête prédéfinie, nommée `Delinquent_Accts`, qui accepte un paramètre pour un nombre de secteur de vente. Cette requête retourne trois colonnes : `Acct_No`, `L_Name`, `Phone`. Toutes les colonnes sont de la table Customers.

Le jeu d’enregistrements suivant spécifie les membres de données de champ pour les colonnes de la requête retourne et un paramètre pour les ventes numéro de secteur demandé au moment de l’exécution.

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

Cette déclaration de classe est telle que l’Assistant, à l’exception de la `m_lDistParam` membre ajouté manuellement. Autres membres ne sont pas affichés ici.

L’exemple suivant illustre les initialisations des membres de données dans le `CDelinquents` constructeur.

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

Remarquez les initialisations de [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) et [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). L’Assistant initialise `m_nFields`; vous initialisez `m_nParams`.

L’exemple suivant montre les fonctions RFX dans `CDelinquents::DoFieldExchange`:

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

Outre les appels RFX pour les trois colonnes retournées, ce code gère la liaison du paramètre que vous passez au moment de l’exécution. Ce paramètre est la clé pour la `Dist_No` colonne (district number).

L’exemple suivant montre comment définir la chaîne SQL et comment l’utiliser pour ouvrir le jeu d’enregistrements.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

Ce code construit un instantané, il passe un paramètre obtenu précédemment à partir de l’utilisateur et appelle la requête prédéfinie. Lorsque la requête s’exécute, elle renvoie les enregistrements pour le secteur de vente spécifié. Chaque enregistrement contient des colonnes pour le numéro de compte et nom du numéro de téléphone du client.

> [!TIP]
>  Vous souhaiterez peut-être gérer une valeur de retour (paramètre de sortie) à partir d’une procédure stockée. Pour plus d’informations et un exemple, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : lancement d’une nouvelle requête sur un recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Recordset : déclaration de la classe d’une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)