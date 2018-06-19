---
title: 'Recordset : Extraction globale d’enregistrements (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ef8803459edeba98e472a0e7fd07e7f5daf2c4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097892"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset : récupération globale d’enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Classe `CRecordset` fournit la prise en charge pour l’extraction de lignes en bloc, ce qui signifie que plusieurs enregistrements peuvent être récupérés à la fois au cours d’une seule extraction, plutôt que de récupérer un seul enregistrement à la fois à partir de la source de données. Vous pouvez implémenter l’extraction de lignes en bloc dans une dérivée `CRecordset` classe. Le processus de transfert de données à partir de la source de données à l’objet de jeu d’enregistrements est appelé RFX en bloc (RFX en bloc). Notez que si vous n’utilisez pas l’extraction de lignes en bloc dans un `CRecordset`-classe dérivée, les données est transférée via l’échange de champs d’enregistrements (RFX). Pour plus d’informations, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
 Cette rubrique explique :  
  
-   [Comment CRecordset prend en charge l’extraction de lignes en bloc](#_core_how_crecordset_supports_bulk_row_fetching).  
  
-   [L’extraction de lignes en bloc des considérations particulières lors de l’utilisation](#_core_special_considerations).  
  
-   [L’implémentation de RFX en bloc](#_core_how_to_implement_bulk_record_field_exchange).  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> Comment CRecordset prend en charge l’extraction de lignes en bloc  
 Avant d’ouvrir l’objet recordset, vous pouvez définir une taille d’ensemble de lignes avec le `SetRowsetSize` fonction membre. La taille de l’ensemble de lignes spécifie le nombre d’enregistrements qui doit être récupéré au cours d’une seule extraction. Lors de l’extraction de lignes en bloc est implémentée, la taille d’ensemble de lignes par défaut est 25. Si l’extraction de lignes en bloc n’est pas implémentée, la taille de l’ensemble de lignes reste fixe à 1.  
  
 Une fois que vous avez initialisé la taille de l’ensemble de lignes, appelez le [ouvrir](../../mfc/reference/crecordset-class.md#open) fonction membre. Ici, vous devez spécifier le `CRecordset::useMultiRowFetch` option de le **dwOptions** paramètre pour implémenter l’extraction de lignes en bloc. Vous pouvez en outre définir le **CRecordset::userAllocMultiRowBuffers** option. Le mécanisme d’échange de champs d’enregistrements en bloc utilise des tableaux pour stocker les lignes de données extraites pendant une extraction. Ces mémoires tampons de stockage peuvent être alloués automatiquement par l’infrastructure, ou vous pouvez allouer manuellement. En spécifiant le **CRecordset::userAllocMultiRowBuffers** option signifie que vous ferez l’allocation.  
  
 Le tableau suivant répertorie les fonctions membres fournies par `CRecordset` pour prendre en charge de l’extraction de lignes en bloc.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Fonction virtuelle qui gère les erreurs qui se produisent pendant l’extraction.|  
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|RFX en bloc les implémente. Appelée automatiquement pour transférer plusieurs lignes de données à partir de la source de données à l’objet recordset.|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Récupère la valeur actuelle de la taille de l’ensemble de lignes.|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indique le nombre de lignes réellement récupéré après une extraction donnée. Dans la plupart des cas, il s’agit de la taille de l’ensemble de lignes, sauf si un ensemble de lignes incomplet a été extrait.|  
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Retourne un état d’extraction pour une ligne particulière dans un ensemble de lignes.|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Actualise les données et l’état d’une ligne particulière dans un ensemble de lignes.|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Déplace le curseur d’une ligne particulière dans un ensemble de lignes.|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Fonction virtuelle qui modifie la valeur de la taille de l’ensemble de lignes à la valeur spécifiée.|  
  
##  <a name="_core_special_considerations"></a> Considérations spéciales  
 Bien que l’extraction de lignes en bloc est un gain de performances, certaines caractéristiques fonctionnent différemment. Avant de décider d’implémenter l’extraction de lignes en bloc, considérez les points suivants :  
  
-   L’infrastructure appelle automatiquement la `DoBulkFieldExchange` fonction membre pour transférer des données à partir de la source de données à l’objet recordset. Toutefois, les données ne sont pas transférées à partir de l’ensemble d’enregistrements dans la source de données. Appel de la `AddNew`, **modifier**, **supprimer**, ou **mise à jour** résultats de fonctions membres dans un échec d’assertion. Bien que `CRecordset` actuellement ne fournit pas un mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**. Pour plus d’informations sur **SQLSetPos**, consultez la *de référence du programmeur ODBC SDK* dans la documentation MSDN.  
  
-   Les fonctions membres `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, et `SetFieldNull` ne peut pas être utilisé sur les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc. Toutefois, vous pouvez appeler `GetRowStatus` à la place de `IsDeleted`, et `GetODBCFieldInfo` à la place de `IsFieldNullable`.  
  
-   Le **déplacer** opérations repositionne le jeu d’enregistrements par ensemble de lignes. Par exemple, supposons que vous ouvrez un jeu d’enregistrements de 100 enregistrements avec une taille d’ensemble de lignes initiale de 10. **Ouvrez** extrait les lignes 1 à 10, avec l’enregistrement actif est positionné sur la ligne 1. Un appel à `MoveNext` extrait l’ensemble de lignes suivant, pas la ligne suivante. Cet ensemble de lignes se compose des lignes 11 à 20, avec l’enregistrement actif positionné sur la ligne 11. Notez que `MoveNext` et **Move (1)** ne sont pas équivalents lorsque l’extraction de lignes en bloc est implémentée. **Move (1)** extrait l’ensemble de lignes qui commence à 1 ligne à partir de l’enregistrement actif. Dans cet exemple, l’appel **Move (1)** après avoir appelé **ouvrir** extrait l’ensemble de lignes composé de lignes 2 à 11, avec l’enregistrement actif est positionné sur la ligne 2. Pour plus d’informations, consultez la [déplacer](../../mfc/reference/crecordset-class.md#move) fonction membre.  
  
-   Contrairement à l’échange de champs d’enregistrements, les Assistants ne prennent pas charge RFX en bloc. Cela signifie que vous devez déclarer manuellement les membres de données de champ et remplacer manuellement `DoBulkFieldExchange` en écrivant les appels aux fonctions RFX en bloc. Pour plus d’informations, consultez [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md) dans les *Class Library Reference*.  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> L’implémentation de RFX en bloc  
 RFX en bloc transfère un ensemble de lignes de données à partir de la source de données à l’objet recordset. Les fonctions RFX en bloc utilisent des tableaux pour stocker ces données, ainsi que des tableaux pour stocker la longueur de chaque élément de données dans l’ensemble de lignes. Dans votre définition de classe, vous devez définir les membres de données de champ en tant que pointeurs pour accéder aux tableaux de données. En outre, vous devez définir un ensemble de pointeurs pour accéder aux tableaux des longueurs. Tous les membres de données de paramètre ne doivent pas être déclarés en tant que pointeurs ; déclarer des membres de données de paramètre lors de l’utilisation de RFX en bloc sont identique à la déclaration les lors de l’utilisation de RFX. Le code suivant montre un exemple simple :  
  
```  
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
  
 Vous pouvez allouer ces tampons de stockage manuellement ou que l’infrastructure de l’allocation. Pour allouer les tampons vous-même, vous devez spécifier le **CRecordset::userAllocMultiRowBuffers** option de le **dwOptions** paramètre dans le **ouvrir** fonction membre. Veillez à définir la taille des tableaux au moins égale à la taille de l’ensemble de lignes. Si vous souhaitez que l’infrastructure de l’allocation, vous devez initialiser les pointeurs à **NULL.** Cela est généralement le cas dans le constructeur de l’objet recordset :  
  
```  
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
  
 Enfin, vous devez substituer la `DoBulkFieldExchange` fonction membre. Les membres de données de champ, appelez les fonctions RFX en bloc ; tous les membres de données de paramètre, appelez les fonctions RFX. Si vous avez ouvert le jeu d’enregistrements en passant une instruction SQL ou une procédure stockée à **ouvrir**, l’ordre dans lequel vous effectuez les appels RFX en bloc doit correspondre à celui des colonnes dans le jeu d’enregistrements ; de même, l’ordre de la RFX appelle pour paramètres doivent correspondre à celui des paramètres dans l’instruction SQL ou procédure stockée.  
  
```  
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
>  Vous devez appeler la **fermer** fonction membre avant votre dérivée `CRecordset` classe est hors de portée. Cela garantit que toute mémoire allouée par l’infrastructure sont libérées. Il est conseillé de toujours appeler explicitement **fermer**, indépendamment de si vous avez implémenté l’extraction de lignes en bloc.  
  
 Pour plus d’informations sur l’échange de champs d’enregistrements (RFX), consultez [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’utilisation de paramètres, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) et [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

