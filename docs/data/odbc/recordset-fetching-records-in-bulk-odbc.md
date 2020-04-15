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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367027"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset : extraction globale d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

La `CRecordset` classe fournit un soutien pour la mise à l’aller en vrac, ce qui signifie que plusieurs enregistrements peuvent être récupérés à la fois au cours d’un seul aller chercher, plutôt que de récupérer un enregistrement à la fois à partir de la source de données. Vous pouvez implémenter la `CRecordset` ligne en vrac aller chercher seulement dans une classe dérivée. Le processus de transfert des données de la source de données à l’objet de l’enregistreur est appelé échange de champ d’enregistrement en vrac (Bulk RFX). Notez que si vous n’utilisez `CRecordset`pas la ligne en vrac aller chercher dans une classe dérivée, les données sont transférées via l’échange de champ record (RFX). Pour plus d’informations, voir [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Cette rubrique répond aux questions suivantes :

- [Comment CRecordset prend en charge la ligne en vrac aller chercher](#_core_how_crecordset_supports_bulk_row_fetching).

- [Quelques considérations spéciales lors de l’utilisation de la ligne en vrac aller chercher](#_core_special_considerations).

- [Comment mettre en œuvre l’échange de records en vrac sur le terrain](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Comment CRecordset soutient bulk Row Fetching

Avant d’ouvrir votre objet de boîte de `SetRowsetSize` disques, vous pouvez définir une taille de ligne avec la fonction membre. La taille de l’aviron précise le nombre d’enregistrements à récupérer au cours d’un seul aller. Lorsque la ramure en vrac est implémentée, la taille par défaut de l’adage en ligne est de 25. Si la mise à la recherche en vrac n’est pas implémentée, la taille de l’aviron reste fixée à 1.

Une fois que vous avez para paralé la taille de l’aviron, appelez la fonction membre [Open.](../../mfc/reference/crecordset-class.md#open) Ici, vous `CRecordset::useMultiRowFetch` devez spécifier l’option du *paramètre dwOptions* pour implémenter la ligne en vrac aller chercher. Vous pouvez en `CRecordset::userAllocMultiRowBuffers` outre définir l’option. Le mécanisme d’échange de champ d’enregistrement en vrac utilise des tableaux pour stocker les multiples rangées de données récupérées lors d’un aller chercher. Ces tampons de stockage peuvent être attribués automatiquement par le cadre ou vous pouvez les allouer manuellement. Spécifier l’option `CRecordset::userAllocMultiRowBuffers` signifie que vous effectuerez l’allocation.

Le tableau suivant énumère les `CRecordset` fonctions des membres fournies par l’appui de la remise en état des rangées en vrac.

|Fonction membre|Description|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Fonction virtuelle qui gère toutes les erreurs qui se produisent lors de la récupération.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implémente l’échange de records en vrac sur le terrain. Appelé automatiquement pour transférer plusieurs lignes de données de la source de données à l’objet de l’enregistrement.|
|[GetRowsetSize GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Récupère le réglage actuel pour la taille de l’aviron.|
|[GetRowsFetched GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Indique combien de rangées ont été effectivement récupérées après un aller chercher donné. Dans la plupart des cas, il s’agit de la taille de l’aviron, à moins qu’un jeu de ligne incomplet n’ait été récupéré.|
|[GetRowStatus GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Retourne un statut d’aller chercher pour une rangée particulière dans un jeu de rangée.|
|[RefreshRowset (en anglais)](../../mfc/reference/crecordset-class.md#refreshrowset)|Rafraîchit les données et l’état d’une rangée particulière dans un jeu de rangée.|
|[SetRowsetCursorPosition (en anglais)](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Déplace le curseur à une rangée particulière dans un jeu de rangée.|
|[SetRowsetSize SetRowsetSize SetRowsetSize SetRow](../../mfc/reference/crecordset-class.md#setrowsetsize)|Fonction virtuelle qui modifie le paramètre de la taille de l’assaillis à la valeur spécifiée.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Considérations spéciales

Bien que la mise à l’allage en vrac soit un gain de performance, certaines fonctionnalités fonctionnent différemment. Avant de décider de mettre en œuvre la mise en place de la ligne en vrac, considérez ce qui suit:

- Le cadre appelle `DoBulkFieldExchange` automatiquement la fonction membre pour transférer des données de la source de données à l’objet de l’enregistrement. Toutefois, les données ne sont pas transférées de l’enregistrement vers la source de données. Appeler `AddNew`le `Edit` `Delete`, `Update` , , ou les fonctions des membres entraîne une affirmation échouée. Bien `CRecordset` qu’actuellement ne fournit pas un mécanisme pour mettre à jour les lignes en vrac `SQLSetPos`de données, vous pouvez écrire vos propres fonctions en utilisant la fonction ODBC API . Pour plus `SQLSetPos`d’informations sur , voir la *référence du programmeur SDK ODBC* dans la documentation MSDN.

- Le membre `IsDeleted`fonctionne `IsFieldDirty` `IsFieldNull`, `IsFieldNullable` `SetFieldDirty`, `SetFieldNull` , , et ne peut pas être utilisé sur les enregistrements qui implémentent la ligne en vrac aller chercher. Cependant, vous `GetRowStatus` pouvez appeler `IsDeleted`à `GetODBCFieldInfo` la `IsFieldNullable`place de , et à la place de .

- Les `Move` opérations repositionnent votre recordet par ligne. Supposons, par exemple, d’ouvrir un jeu d’enregistrement qui compte 100 enregistrements d’une taille initiale de 10. `Open`récupère les rangées 1 à 10, le record actuel se positionne sur la ligne 1. Un appel `MoveNext` pour aller chercher le jeu de ligne suivant, pas la rangée suivante. Ce ramé se compose de lignes 11 à 20, avec le record actuel positionné sur la rangée 11. Notez `MoveNext` `Move( 1 )` cela et ne sont pas équivalents lorsque la ligne en vrac fetching est implémentée. `Move( 1 )`récupère le rowset qui commence 1 rangée du record actuel. Dans cet exemple, `Move( 1 )` `Open` appeler après avoir appelé récupère le rowset composé de rangées 2 à 11, avec le record actuel positionné sur la rangée 2. Pour plus d’informations, consultez la fonction membre [Move.](../../mfc/reference/crecordset-class.md#move)

- Contrairement à l’échange record sur le terrain, les sorciers ne prennent pas en charge l’échange de records en vrac sur le terrain. Cela signifie que vous devez déclarer manuellement vos `DoBulkFieldExchange` membres de données sur le terrain et passer manuellement en écrivant des appels aux fonctions RFX en vrac. Pour plus d’informations, voir [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md) in the *Class Library Reference*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Comment mettre en œuvre Bulk Record Field Exchange

L’échange de champ d’enregistrement en vrac transfère un ensemble de données de la source de données à l’objet de l’enregistrement. Les fonctions RFX en vrac utilisent des tableaux pour stocker ces données, ainsi que des tableaux pour stocker la longueur de chaque élément de données dans le ramset. Dans votre définition de classe, vous devez définir vos membres de données sur le terrain comme des indications pour accéder aux tableaux de données. En outre, vous devez définir un ensemble de pointeurs pour accéder aux tableaux de longueurs. Les membres des données de paramètres ne doivent pas être déclarés comme pointeurs; déclarer les membres des données de paramètres lors de l’utilisation de l’échange de données en vrac sur le terrain est le même que de les déclarer lors de l’utilisation d’échanges de records sur le terrain. Le code suivant montre un exemple simple :

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

Vous pouvez soit allouer ces tampons de stockage manuellement ou faire en faire le cadre de l’allocation. Pour répartir les tampons vous-même, vous devez spécifier l’option `CRecordset::userAllocMultiRowBuffers` du paramètre *dwOptions* dans la `Open` fonction membre. Assurez-vous de définir les tailles des tableaux au moins égales à la taille de l’acart. Si vous voulez que le cadre fasse l’allocation, vous devriez initialiser vos pointeurs à NULL. Ceci est généralement fait dans le constructeur de l’objet de l’enregistrement :

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

Enfin, vous devez `DoBulkFieldExchange` remplacer la fonction de membre. Pour les membres des données sur le terrain, appelez les fonctions RFX en vrac; pour tous les membres de données de paramètres, appelez les fonctions RFX. Si vous avez ouvert le registre en passant `Open`une déclaration SQL ou une procédure stockée à , l’ordre dans lequel vous effectuez les appels RFX en vrac doit correspondre à l’ordre des colonnes dans le dossier; de même, l’ordre de la RFX prévoit des paramètres doit correspondre à l’ordre des paramètres dans la déclaration SQL ou la procédure stockée.

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
> Vous devez `Close` appeler la fonction `CRecordset` membre avant que votre classe dérivée ne dépasse la portée. Cela garantit que toute mémoire allouée par le cadre est libérée. Il est bon pratique de `Close`programmation d’appeler toujours explicitement, peu importe si vous avez mis en œuvre la ligne en vrac aller chercher.

Pour plus d’informations sur l’échange record sur le terrain (RFX), voir [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’utilisation des paramètres, voir [CFieldExchange:SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) et [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
