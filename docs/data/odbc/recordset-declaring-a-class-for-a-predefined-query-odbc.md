---
description: 'En savoir plus sur : Recordset : déclaration d’une classe pour une requête prédéfinie (ODBC)'
title: "Recordset : déclaration de la classe d'une requête prédéfinie (ODBC)"
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: e2071270bbff92e56b7fc3a2064e7e2f99f2044b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210944"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Recordset : déclaration de la classe d'une requête prédéfinie (ODBC)

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer un consommateur manuellement.

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment créer une classe de recordset pour une requête prédéfinie (parfois appelée procédure stockée, comme dans Microsoft SQL Server).

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si la récupération de lignes en bloc est implémentée, le processus est très similaire. Pour comprendre les différences entre les recordsets qui implémentent l’extraction de lignes en bloc et ceux qui ne le sont pas, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Certains systèmes de gestion de base de données (SGBD) vous permettent de créer une requête prédéfinie et de l’appeler de votre programme comme une fonction. La requête a toujours un nom, et elle peut éventuellement prendre des paramètres et retourner des enregistrements. La procédure dans cette rubrique décrit comment appeler une requête prédéfinie qui retourne des enregistrements (et prend éventuellement des paramètres).

Les classes de base de données ne prennent pas en charge la mise à jour des requêtes prédéfinies. La différence entre une requête prédéfinie instantanée et une requête prédéfinie dynamique n’est pas la possibilité de mise à jour, mais plutôt la possibilité de voir dans le recordset les modifications apportées par d’autres utilisateurs (ou d’autres recordsets dans votre programme).

> [!TIP]
> L’utilisation d’un recordset n’est pas nécessaire pour appeler une requête prédéfinie qui ne retourne pas d’enregistrements. Préparez l’instruction SQL comme cela est décrit ci-dessous, mais exécutez-la en appelant la fonction membre `CDatabase`[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Vous pouvez créer une seule classe de recordset pour gérer l’appel d’une requête prédéfinie, mais vous devez alors faire une partie du travail manuellement. Les Assistants ne prennent pas en charge la création d’une classe spécialement conçue à cet effet.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Pour créer une classe permettant d’appeler une requête prédéfinie (procédure stockée)

1. Utilisez l’[Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)**Ajouter une classe** afin de créer une classe de recordset pour la table dont proviennent la plupart des colonnes retournées par la requête. Cela vous permet de démarrer rapidement.

1. Ajoutez manuellement les membres de données de champ pour toutes les colonnes de tables qui sont retournées par la requête mais que l’Assistant n’a pas créées pour vous.

   Par exemple, si la requête retourne trois colonnes de deux tables supplémentaires, ajoutez six membres de données de champ (des types de données appropriés) à la classe.

1. Ajoutez manuellement les appels de fonction [RFX](../../data/odbc/record-field-exchange-rfx.md) dans la fonction membre [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) de la classe, correspondant chacun au type de données de chaque membre de données de champ ajouté.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Vous devez connaître les types de données et l’ordre des colonnes retournées dans le jeu de résultats. L’ordre des appels de fonction RFX dans `DoFieldExchange` doit correspondre à l’ordre des colonnes du jeu de résultats.

1. Ajoutez manuellement des initialisations pour les nouveaux membres de données de champ dans le constructeur de classe de recordset.

   Vous devez également incrémenter la valeur d’initialisation pour le membre de données [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). L’Assistant écrit l’initialisation, mais uniquement pour les membres de données de champ qu’il ajoute automatiquement. Par exemple :

    ```cpp
    m_nFields += 6;
    ```

   Certains types de données ne doivent pas être initialisés ici, comme `CLongBinary` ou les tableaux d’octets.

1. Si la requête prend des paramètres, ajoutez un membre de données de paramètre pour chaque paramètre, ainsi qu’un appel de fonction RFX et une initialisation pour chacun.

1. Vous devez incrémenter `m_nParams` pour chaque paramètre ajouté, comme vous avez incrémenté `m_nFields` pour les champs ajoutés à l’étape 4 de cette procédure. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ajoutez manuellement une chaîne d’instruction SQL au format suivant :

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   où **CALL** est un mot clé ODBC, **proc-name** est le nom de la requête tel qu’il est connu dans la source de données, et les éléments « ? » sont des espaces réservés pour les valeurs de paramètre que vous fournissez au recordset au moment de l’exécution (le cas échéant). L’exemple suivant prépare un espace réservé pour un seul paramètre :

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. Dans le code qui ouvre le recordset, définissez les valeurs des membres de données de paramètre du recordset, puis appelez la fonction membre `Open`, en passant la chaîne SQL pour le paramètre *lpszSQL*. Ou bien, remplacez la chaîne retournée par la fonction membre `GetDefaultSQL` dans votre classe.

Les exemples suivants montrent la procédure d’appel d’une requête prédéfinie, nommée `Delinquent_Accts`, qui prend un paramètre correspondant au numéro du secteur de vente. Cette requête retourne trois colonnes : `Acct_No`, `L_Name` et `Phone`. Toutes les colonnes proviennent de la table Customers.

Le recordset suivant spécifie les membres de données de champ pour les colonnes retournées par la requête ainsi qu’un paramètre correspondant au numéro de secteur de vente demandé au moment de l’exécution.

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

Cette déclaration de classe est telle qu’elle a été écrite par l’Assistant, à l’exception du membre `m_lDistParam` ajouté manuellement. Les autres membres ne sont pas présentés ici.

L’exemple suivant montre les initialisations pour les membres de données dans le constructeur `CDelinquents`.

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

Notez la présence des initialisations pour [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) et [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). L’Assistant initialise `m_nFields` et vous, vous initialisez `m_nParams`.

L’exemple suivant montre les fonctions RFX dans `CDelinquents::DoFieldExchange` :

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

Ce code effectue les appels de fonction RFX pour les trois colonnes retournées et il gère la liaison du paramètre que vous passez au moment de l’exécution. Ce paramètre est associé à la colonne `Dist_No` (numéro du secteur).

L’exemple suivant montre comment définir la chaîne SQL et comment l’utiliser pour ouvrir le recordset.

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

Ce code construit un instantané, passe à cet instantané un paramètre obtenu précédemment de l’utilisateur et appelle la requête prédéfinie. À l’exécution de la requête, il retourne les enregistrements correspondant au secteur de vente spécifié. Chaque enregistrement contient les colonnes pour le numéro de compte, le nom du client et le numéro de téléphone du client.

> [!TIP]
> Vous pouvez avoir besoin de gérer une valeur (paramètre de sortie) retournée par une procédure stockée. Pour plus d’informations et obtenir un exemple, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : rerequête d’un Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Recordset : déclaration d’une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset : exécution d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
