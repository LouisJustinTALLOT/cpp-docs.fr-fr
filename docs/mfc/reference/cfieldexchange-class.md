---
title: Classe CFieldExchange
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: d4b99a4992075072253d4f9b3182a926673bdfd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373930"
---
# <a name="cfieldexchange-class"></a>Classe CFieldExchange

Prend en charge les routines d'échange de champs d'enregistrements (RFX) et d'échange de champs d'enregistrements en bloc (RFX en bloc) utilisées par les classes de base de données.

## <a name="syntax"></a>Syntaxe

```
class CFieldExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Retourne nonzero si l’opération actuelle est appropriée pour le type de champ mis à jour.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Spécifie le type de membre des données de l’enregistrement — colonne ou paramètre `SetFieldType`— représenté par tous les appels suivants aux fonctions RFX jusqu’au prochain appel à .|

## <a name="remarks"></a>Notes

`CFieldExchange`n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour des types de données personnalisés ou lorsque vous implémentez des saisies en vrac; sinon, vous n’utiliserez pas directement cette classe. RFX et RFX en vrac échangent des données entre les membres des données sur le terrain de votre objet de numérotation et les champs correspondants de l’enregistrement actuel sur la source de données.

> [!NOTE]
> Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt qu’avec les classes de connectivité à base de données ouvertes (ODBC), utilisez plutôt la classe [CDaoFieldExchange.](../../mfc/reference/cdaofieldexchange-class.md) Pour plus d’informations, voir l’article [Aperçu:Database Programming](../../data/data-access-programming-mfc-atl.md).

Un `CFieldExchange` objet fournit l’information contextuelle nécessaire à l’échange de documents sur le terrain ou à l’échange de dossiers en vrac. `CFieldExchange`les objets prennent en charge un certain nombre d’opérations, y compris les paramètres contraignants et les membres des données sur le terrain et l’établissement de divers drapeaux sur les champs du dossier actuel. Les opérations RFX et Bulk RFX sont effectuées sur des données de classe `CFieldExchange`record de types définis par **l’enum** **FieldType** dans . Les valeurs possibles **de FieldType** sont les :

- `CFieldExchange::outputColumn`pour les membres des données sur le terrain.

- `CFieldExchange::inputParam`ou `CFieldExchange::param` pour les membres des données de paramètres d’entrée.

- `CFieldExchange::outputParam`pour les membres des données de paramètres de sortie.

- `CFieldExchange::inoutParam`pour les membres des données de paramètres d’entrée/sortie.

La plupart des fonctions des membres et des membres de la classe sont fournis pour écrire vos propres routines RFX personnalisées. Vous utiliserez `SetFieldType` fréquemment. Pour plus d’informations, voir les articles [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur la ligne en vrac aller chercher, voir l’article [Recordset: Fetching Records en vrac (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus de détails sur les fonctions mondiales RFX et Bulk RFX, voir [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md) dans la section MFC Macros et Globals de cette référence.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CFieldExchange`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::IsFieldType

Si vous écrivez votre propre `IsFieldType` fonction RFX, appelez au début de votre fonction pour déterminer si l’opération `CFieldExchange::outputParam`actuelle `CFieldExchange::inoutParam`peut être effectuée sur un champ particulier ou le type de membre de données de paramètre (a `CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, , ou ).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Paramètres

*pnField (en)*<br/>
Le nombre séquentiel du membre des données de champ ou de paramètre est retourné dans ce paramètre. Ce nombre correspond à l’ordre du membre des données dans la fonction [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) fonction.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération actuelle peut être effectuée sur le champ actuel ou le type de paramètre.

### <a name="remarks"></a>Notes

Suivez le modèle des fonctions RFX existantes.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange::SetFieldType

Vous avez besoin `SetFieldType` d’un appel dans [doFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) de votre classe de disques.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Paramètres

*nFieldType (en)*<br/>
Une valeur `enum FieldType`du , `CFieldExchange`déclaré en , qui peut être l’un des suivants:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Notes

Pour les membres de `SetFieldType` données sur `CFieldExchange::outputColumn`le terrain, vous devez appeler avec un paramètre de , suivie d’appels vers les fonctions RFX ou Bulk RFX. Si vous n’avez pas implémenté la `SetFieldType` ligne en vrac aller `DoFieldExchange`chercher, puis ClassWizard place cet appel pour vous dans la section de carte de champ de .

Si vous paramétisez votre `SetFieldType` classe de jeu d’enregistrement, vous devez appeler à nouveau, en dehors de n’importe quelle section de carte de champ, suivie par les appels RFX pour tous les membres de données de paramètres. Chaque type de membre des `SetFieldType` données de paramètres doit avoir son propre appel. Le tableau suivant distingue les différentes valeurs `SetFieldType` que vous pouvez transmettre pour représenter les données de paramètres des membres de votre classe :

|Valeur du paramètre SetFieldType|Type de membre des données de paramètres|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Paramètre d’entrée. Une valeur qui est transmise dans la requête du dossier ou la procédure stockée.|
|`CFieldExchange::param` | même `CFieldExchange::inputParam`que .|
|`CFieldExchange::outputParam`|Paramètre de sortie. Une valeur de retour de la procédure stockée du recordet.|
|`CFieldExchange::inoutParam`|Paramètres d’entrée/sortie. Une valeur qui est transmise et retournée de la procédure stockée du recordet.|

En général, chaque groupe d’appels de fonction RFX associés aux membres de `SetFieldType`données sur le terrain ou aux données de paramètres membres doit être précédé d’un appel à . Le paramètre *nFieldType* de chaque `SetFieldType` appel identifie le type de données représentées `SetFieldType` par les appels de fonction RFX qui suivent l’appel.

Pour plus d’informations sur le traitement des `CRecordset` paramètres de sortie et d’entrée/sortie, consultez la fonction membre [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Pour plus d’informations sur les fonctions RFX et Bulk RFX, consultez le sujet [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations connexes sur la ligne en vrac aller chercher, voir l’article [Recordset: Fetching Records en vrac (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

Cet exemple montre plusieurs appels aux fonctions `SetFieldType`RFX avec des appels d’accompagnement à . Notez `SetFieldType` que c’est appelé à travers le `pFX` pointeur à un `CFieldExchange` objet.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
