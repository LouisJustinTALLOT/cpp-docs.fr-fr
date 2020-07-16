---
title: "Recordset : extraction globale d'enregistrements (ODBC)"
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
ms.openlocfilehash: ccdc4668f0c19f63ec86ee9a6d788532eb4d9d38
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403710"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset : extraction globale d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

`CRecordset`La classe fournit la prise en charge de l’extraction de lignes en bloc, ce qui signifie que plusieurs enregistrements peuvent être récupérés à la fois pendant une seule extraction, au lieu de récupérer un enregistrement à la fois à partir de la source de données. Vous pouvez implémenter l’extraction de lignes en bloc uniquement dans une classe dérivée `CRecordset` . Le processus de transfert de données de la source de données vers l’objet Recordset est appelé échange de champs d’enregistrements en bloc (RFX en bloc). Notez que si vous n’utilisez pas l’extraction de lignes en bloc dans une `CRecordset` classe dérivée de, les données sont transférées via RFX (Record Field Exchange). Pour plus d’informations, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Cette rubrique répond aux questions suivantes :

- [Comment CRecordset prend en charge l’extraction de lignes en bloc](#_core_how_crecordset_supports_bulk_row_fetching).

- [Considérations particulières lors de l’utilisation de l’extraction de lignes en bloc](#_core_special_considerations).

- [Comment implémenter l’échange de champs d’enregistrements en bloc](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Comment CRecordset prend en charge l’extraction de lignes en bloc

Avant d’ouvrir l’objet Recordset, vous pouvez définir une taille d’ensemble de lignes avec la `SetRowsetSize` fonction membre. La taille de l’ensemble de lignes spécifie le nombre d’enregistrements qui doivent être récupérés au cours d’une seule extraction. Lorsque l’extraction de lignes en bloc est implémentée, la taille de l’ensemble de lignes par défaut est 25. Si l’extraction de lignes en bloc n’est pas implémentée, la taille de l’ensemble de lignes reste fixée à 1.

Après avoir initialisé la taille de l’ensemble de lignes, appelez la fonction membre [Open](../../mfc/reference/crecordset-class.md#open) . Ici, vous devez spécifier l' `CRecordset::useMultiRowFetch` option du paramètre *dwOptions* pour implémenter l’extraction de lignes en bloc. Vous pouvez également définir l' `CRecordset::userAllocMultiRowBuffers` option. Le mécanisme d’échange de champs d’enregistrements en bloc utilise des tableaux pour stocker les nombreuses lignes de données récupérées lors d’une extraction. Ces mémoires tampons de stockage peuvent être allouées automatiquement par l’infrastructure ou vous pouvez les allouer manuellement. La spécification de l' `CRecordset::userAllocMultiRowBuffers` option signifie que vous allez effectuer l’allocation.

Le tableau suivant répertorie les fonctions membres fournies par `CRecordset` pour prendre en charge l’extraction de lignes en bloc.

|Fonction membre|Description|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Fonction virtuelle qui gère toutes les erreurs qui se produisent pendant l’extraction.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implémente l’échange de champs d’enregistrements en bloc. Appelé automatiquement pour transférer plusieurs lignes de données de la source de données vers l’objet Recordset.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Récupère le paramètre actuel pour la taille de l’ensemble de lignes.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indique le nombre de lignes réellement récupérées après une extraction donnée. Dans la plupart des cas, il s’agit de la taille de l’ensemble de lignes, sauf si un ensemble de lignes incomplet a été extrait.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Retourne l’état d’extraction d’une ligne particulière au sein d’un ensemble de lignes.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualise les données et l’état d’une ligne particulière au sein d’un ensemble de lignes.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Déplace le curseur vers une ligne particulière au sein d’un ensemble de lignes.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Fonction virtuelle qui modifie la valeur du paramètre pour la taille de l’ensemble de lignes à la valeur spécifiée.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Considérations spéciales

Bien que l’extraction de lignes en bloc soit un gain de performances, certaines fonctionnalités fonctionnent différemment. Avant de décider d’implémenter l’extraction de lignes en bloc, tenez compte des éléments suivants :

- L’infrastructure appelle automatiquement la `DoBulkFieldExchange` fonction membre pour transférer des données de la source de données vers l’objet Recordset. Toutefois, les données ne sont pas transférées du recordset vers la source de données. L’appel `AddNew` des `Edit` `Delete` fonctions membres,, ou `Update` entraîne l’échec d’une assertion. Bien que `CRecordset` ne fournisse actuellement pas de mécanisme de mise à jour des lignes de données en bloc, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos` . Pour plus d’informations sur `SQLSetPos` , consultez le [Guide de référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference).

- Les fonctions membres,,,, `IsDeleted` `IsFieldDirty` `IsFieldNull` `IsFieldNullable` `SetFieldDirty` et `SetFieldNull` ne peuvent pas être utilisées sur les recordsets qui implémentent l’extraction de lignes en bloc. Toutefois, vous pouvez appeler `GetRowStatus` à la place de `IsDeleted` et `GetODBCFieldInfo` à la place de `IsFieldNullable` .

- Les `Move` opérations repositionnent votre Recordset par ensemble de lignes. Par exemple, supposons que vous ouvrez un jeu d’enregistrements qui contient 100 enregistrements avec une taille d’ensemble de lignes initiale de 10. `Open`extrait les lignes 1 à 10, avec l’enregistrement en cours positionné sur la ligne 1. Appel pour `MoveNext` extraire l’ensemble de lignes suivant, et non la ligne suivante. Cet ensemble de lignes se compose de lignes 11 à 20, avec l’enregistrement en cours positionné sur la ligne 11. Notez que `MoveNext` et ne `Move( 1 )` sont pas équivalents lorsque l’extraction de lignes en bloc est implémentée. `Move( 1 )`extrait l’ensemble de lignes qui commence la ligne 1 de l’enregistrement en cours. Dans cet exemple, l’appel à `Move( 1 )` après `Open` l’appel de récupère l’ensemble de lignes composé de lignes 2 à 11, avec l’enregistrement actuel positionné sur la ligne 2. Pour plus d’informations, consultez la fonction de [déplacement](../../mfc/reference/crecordset-class.md#move) de membre.

- Contrairement à l’échange de champs d’enregistrement, les assistants ne prennent pas en charge l’échange de champs d’enregistrements en bloc. Cela signifie que vous devez déclarer manuellement les membres de données de champ et les remplacer manuellement `DoBulkFieldExchange` en écrivant des appels aux fonctions RFX en bloc. Pour plus d’informations, consultez [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md) dans la référence de la *bibliothèque de classes*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Comment implémenter l’échange de champs d’enregistrements en bloc

L’échange de champs d’enregistrements en bloc transfère un ensemble de lignes de données de la source de données vers l’objet Recordset. Les fonctions RFX en bloc utilisent des tableaux pour stocker ces données, ainsi que des tableaux pour stocker la longueur de chaque élément de données dans l’ensemble de lignes. Dans votre définition de classe, vous devez définir les membres de données de champ comme pointeurs pour accéder aux tableaux de données. En outre, vous devez définir un ensemble de pointeurs pour accéder aux tableaux de longueurs. Les membres de données de paramètre ne doivent pas être déclarés comme pointeurs ; la déclaration de membres de données de paramètre lors de l’utilisation de l’échange de champs d’enregistrements en bloc revient à les déclarer lors de l’utilisation d’un échange de champs d’enregistrement. Le code suivant illustre un exemple simple :

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

Vous pouvez soit allouer ces mémoires tampons de stockage manuellement, soit faire en sorte que l’infrastructure effectue l’allocation. Pour allouer les tampons vous-même, vous devez spécifier l' `CRecordset::userAllocMultiRowBuffers` option du paramètre *dwOptions* dans la `Open` fonction membre. Veillez à définir les tailles des tableaux au moins égal à la taille de l’ensemble de lignes. Si vous souhaitez que le Framework fasse l’allocation, vous devez initialiser vos pointeurs sur la valeur NULL. Cela s’effectue généralement dans le constructeur de l’objet Recordset :

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

Enfin, vous devez substituer la `DoBulkFieldExchange` fonction membre. Pour les membres de données de champ, appelez les fonctions RFX en bloc. pour les membres de données de paramètre, appelez les fonctions RFX. Si vous avez ouvert le Recordset en passant une instruction SQL ou une procédure stockée à `Open` , l’ordre dans lequel vous effectuez les appels RFX en bloc doit correspondre à l’ordre des colonnes dans le Recordset. de même, l’ordre des appels RFX pour les paramètres doit correspondre à l’ordre des paramètres dans l’instruction SQL ou la procédure stockée.

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
> Vous devez appeler la `Close` fonction membre avant que votre classe dérivée ne soit `CRecordset` hors de portée. Cela garantit que toute mémoire allouée par l’infrastructure est libérée. Il est recommandé de toujours appeler explicitement `Close` , que vous ayez implémenté l’extraction de lignes en bloc ou non.

Pour plus d’informations sur RFX (Record Field Exchange), consultez [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’utilisation des paramètres, consultez [CFieldExchange :: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) et [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset :: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset :: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
