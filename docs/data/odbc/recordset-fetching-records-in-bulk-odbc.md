---
title: 'Recordset : Extraction globale d’enregistrements en bloc (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: 2fdcbf18fcb0d97ba7b2a39aa9bbbd79e65a4112
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397846"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset : Extraction globale d’enregistrements en bloc (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Classe `CRecordset` prend en charge l’extraction de lignes en bloc, ce qui signifie que plusieurs enregistrements peuvent être extraites en une seule fois pendant une extraction unique, plutôt que de récupérer un seul enregistrement à la fois la source de données. Vous pouvez implémenter l’extraction de lignes en bloc dans une dérivée `CRecordset` classe. Le processus de transfert de données à partir de la source de données à l’objet de jeu d’enregistrements est appelé RFX en bloc (RFX en bloc). Notez que si vous n’utilisez pas l’extraction de lignes en bloc dans un `CRecordset`-classe dérivée, les données est transférée via l’échange de champs d’enregistrements (RFX). Pour plus d’informations, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Cette rubrique explique :

- [Comment CRecordset prend en charge l’extraction de lignes en bloc](#_core_how_crecordset_supports_bulk_row_fetching).

- [Extraction de lignes en bloc des considérations particulières lors de l’utilisation](#_core_special_considerations).

- [L’implémentation de RFX en bloc](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> Comment CRecordset prend en charge l’extraction de lignes en bloc

Avant d’ouvrir l’objet recordset, vous pouvez définir une taille d’ensemble de lignes avec le `SetRowsetSize` fonction membre. La taille de l’ensemble de lignes spécifie le nombre d’enregistrements doit être récupéré pendant une extraction unique. Lors de l’extraction de lignes en bloc est implémentée, la taille d’ensemble de lignes par défaut est 25. Si l’extraction de lignes en bloc n’est pas implémentée, la taille de l’ensemble de lignes reste fixe à 1.

Une fois que vous avez initialisé la taille de l’ensemble de lignes, appelez le [Open](../../mfc/reference/crecordset-class.md#open) fonction membre. Ici, vous devez spécifier le `CRecordset::useMultiRowFetch` possibilité du *dwOptions* paramètre pour implémenter l’extraction de lignes en bloc. Vous pouvez en outre définir la `CRecordset::userAllocMultiRowBuffers` option. Le mécanisme d’échange de champs d’enregistrements en bloc utilise des tableaux pour stocker les lignes de données récupérées lors d’une extraction. Ces mémoires tampons de stockage peuvent être alloués automatiquement par l’infrastructure, ou vous pouvez les allouer manuellement. Spécifiant la `CRecordset::userAllocMultiRowBuffers` option signifie que vous effectuerez l’allocation.

Le tableau suivant répertorie les fonctions membres fournies par `CRecordset` pour prendre en charge l’extraction de lignes en bloc.

|Fonction membre|Description|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Fonction virtuelle qui gère les erreurs qui se produisent pendant l’extraction.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implémente mécanisme RFX en bloc. Appelée automatiquement pour transférer plusieurs lignes de données à partir de la source de données à l’objet recordset.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Récupère la valeur actuelle de la taille de l’ensemble de lignes.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indique le nombre de lignes réellement récupéré après une extraction donnée. Dans la plupart des cas, il s’agit de la taille de l’ensemble de lignes, sauf si un ensemble de lignes incomplète a été extrait.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Retourne un état d’extraction pour une ligne particulière au sein d’un ensemble de lignes.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualise les données et l’état d’une ligne particulière dans un ensemble de lignes.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Déplace le curseur à une ligne particulière au sein d’un ensemble de lignes.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Fonction virtuelle qui modifie le paramètre de la taille de l’ensemble de lignes à la valeur spécifiée.|

##  <a name="_core_special_considerations"></a> Considérations spéciales

Bien que l’extraction de lignes en bloc est un gain de performances, certaines fonctionnalités qu’elles fonctionnent différemment. Avant de décider d’implémenter l’extraction de lignes en bloc, considérez les points suivants :

- L’infrastructure appelle automatiquement la `DoBulkFieldExchange` fonction membre pour transférer des données à partir de la source de données vers l’objet recordset. Toutefois, les données ne sont pas transférées à partir de l’ensemble d’enregistrements à la source de données. Appel de la `AddNew`, `Edit`, `Delete`, ou `Update` résultats de fonctions de membre dans un échec d’assertion. Bien que `CRecordset` actuellement ne fournit pas un mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur `SQLSetPos`, consultez le *de référence du programmeur ODBC SDK* dans la documentation MSDN.

- Les fonctions membres `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, et `SetFieldNull` ne peut pas être utilisé sur les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc. Toutefois, vous pouvez appeler `GetRowStatus` à la place de `IsDeleted`, et `GetODBCFieldInfo` à la place de `IsFieldNullable`.

- Le `Move` opérations repositionne le jeu d’enregistrements par jeu de lignes. Par exemple, supposons que vous ouvrez un jeu d’enregistrements de 100 enregistrements avec une taille d’ensemble de lignes initiale de 10. `Open` extrait les lignes 1 à 10, avec l’enregistrement actif positionnés sur la ligne 1. Un appel à `MoveNext` extrait l’ensemble de lignes suivant, pas la ligne suivante. Cet ensemble de lignes se compose des lignes 11 à 20, avec l’enregistrement actif positionné sur la ligne 11. Notez que `MoveNext` et `Move( 1 )` ne sont pas équivalents lorsque l’extraction de lignes en bloc est implémentée. `Move( 1 )` extrait l’ensemble de lignes qui commence à 1 ligne à partir de l’enregistrement actif. Dans cet exemple, l’appel `Move( 1 )` après l’appel `Open` extrait l’ensemble de lignes composé de lignes 2 à 11, avec l’enregistrement actif est positionné sur la ligne 2. Pour plus d’informations, consultez le [déplacer](../../mfc/reference/crecordset-class.md#move) fonction membre.

- Contrairement à l’échange de champs d’enregistrements, les Assistants ne gèrent pas RFX en bloc. Cela signifie que vous devez déclarer manuellement les membres de données de champ et substituer manuellement `DoBulkFieldExchange` en écrivant les appels aux fonctions RFX en bloc. Pour plus d’informations, consultez [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md) dans le *Class Library Reference*.

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> L’implémentation de RFX en bloc

RFX en bloc transfère un ensemble de lignes de données à partir de la source de données à l’objet recordset. Les fonctions RFX en bloc utilisent des tableaux pour stocker ces données, ainsi que des tableaux pour stocker la longueur de chaque élément de données dans l’ensemble de lignes. Dans votre définition de classe, vous devez définir les membres de données de champ en tant que pointeurs pour accéder aux tableaux de données. En outre, vous devez définir un ensemble de pointeurs pour accéder aux tableaux des longueurs. Aucun membre de données de paramètre ne doit pas être déclaré en tant que pointeurs ; déclarer les membres de données de paramètre lors de l’utilisation de RFX en bloc est identique à les déclarant lors de l’utilisation d’échange de champs d’enregistrements. Le code suivant montre un exemple simple :

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

Vous pouvez allouer ces tampons de stockage manuellement ou que l’infrastructure de l’allocation. Pour allouer les tampons vous-même, vous devez spécifier le `CRecordset::userAllocMultiRowBuffers` possibilité du *dwOptions* paramètre dans le `Open` fonction membre. Veillez à définir les tailles des tableaux au moins égale à la taille de l’ensemble de lignes. Si vous souhaitez que l’infrastructure de l’allocation, vous devez initialiser les pointeurs avec la valeur NULL. Cela s’effectue généralement dans le constructeur de l’objet jeu d’enregistrements :

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

Enfin, vous devez substituer la `DoBulkFieldExchange` fonction membre. Pour les membres de données de champ, appelez les fonctions RFX en bloc ; pour les membres de données de paramètre, appelez les fonctions RFX. Si vous avez ouvert le jeu d’enregistrements en transmettant une instruction SQL ou une procédure stockée à `Open`, l’ordre dans lequel vous effectuez les appels RFX en bloc doit correspondre à celui des colonnes dans le jeu d’enregistrements ; de même, l’ordre du appels RFX pour les paramètres doivent correspondre à l’ordre des paramètres dans l’instruction SQL ou une procédure stockée.

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  Vous devez appeler la `Close` fonction membre avant votre dérivée `CRecordset` classe est hors de portée. Cela garantit que toute mémoire allouée par l’infrastructure sont libérées. Il est conseillé de toujours appeler explicitement `Close`, indépendamment de si vous avez implémenté l’extraction de lignes en bloc.

Pour plus d’informations sur l’échange de champs d’enregistrements (RFX), consultez [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’utilisation de paramètres, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) et [jeu d’enregistrements : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

