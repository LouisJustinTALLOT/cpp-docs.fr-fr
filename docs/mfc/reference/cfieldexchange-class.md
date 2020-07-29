---
title: CFieldExchange, classe
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
ms.openlocfilehash: d10bfc436297a5f861f17843007347dcef9e58ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212473"
---
# <a name="cfieldexchange-class"></a>CFieldExchange, classe

Prend en charge les routines d'échange de champs d'enregistrements (RFX) et d'échange de champs d'enregistrements en bloc (RFX en bloc) utilisées par les classes de base de données.

## <a name="syntax"></a>Syntaxe

```
class CFieldExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFieldExchange :: IsFieldType](#isfieldtype)|Retourne une valeur différente de zéro si l’opération en cours est appropriée pour le type de champ en cours de mise à jour.|
|[CFieldExchange :: SetFieldType](#setfieldtype)|Spécifie le type de membre de données du jeu d’enregistrements (colonne ou paramètre) représenté par tous les appels suivants aux fonctions RFX jusqu’au prochain appel à `SetFieldType` .|

## <a name="remarks"></a>Notes

`CFieldExchange`n’a pas de classe de base.

Utilisez cette classe si vous écrivez des routines d’échange de données pour des types de données personnalisés ou lorsque vous implémentez l’extraction de lignes en bloc. dans le cas contraire, vous n’utiliserez pas directement cette classe. RFX et RFX en bloc échangent des données entre les membres de données de champ de votre objet Recordset et les champs correspondants de l’enregistrement actif sur la source de données.

> [!NOTE]
> Si vous utilisez les classes DAO (Data Access Objects) au lieu des classes Open Database Connectivity (ODBC), utilisez la classe [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

Un `CFieldExchange` objet fournit les informations de contexte nécessaires à l’échange de champs d’enregistrement ou à l’échange de champs d’enregistrement en bloc. `CFieldExchange`les objets prennent en charge un certain nombre d’opérations, y compris les paramètres de liaison et les membres de données de champ, et la définition de différents indicateurs sur les champs de l’enregistrement actif. Les opérations RFX et RFX en bloc sont effectuées sur les membres de données de classe Recordset de types définis par l’argument **`enum`** **FieldType** dans `CFieldExchange` . Les valeurs possibles de **FieldType** sont les suivantes :

- `CFieldExchange::outputColumn`pour les membres de données de champ.

- `CFieldExchange::inputParam`ou `CFieldExchange::param` pour les membres de données de paramètre d’entrée.

- `CFieldExchange::outputParam`pour les membres de données de paramètre de sortie.

- `CFieldExchange::inoutParam`pour les membres de données de paramètre d’entrée/sortie.

La plupart des fonctions membres et membres de données de la classe sont fournis pour l’écriture de vos propres routines RFX personnalisées. Vous utiliserez `SetFieldType` fréquemment. Pour plus d’informations, consultez les articles [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations sur les fonctions RFX et les fonctions globales RFX en bloc, consultez [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md) dans la section macros MFC et globales de cette référence.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CFieldExchange`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange :: IsFieldType

Si vous écrivez votre propre fonction RFX, appelez `IsFieldType` au début de votre fonction pour déterminer si l’opération en cours peut être effectuée sur un champ ou un type de membre de données de paramètre particulier (un `CFieldExchange::outputColumn` , `CFieldExchange::inputParam` ,, `CFieldExchange::param` `CFieldExchange::outputParam` ou `CFieldExchange::inoutParam` ).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Paramètres

*pnField*<br/>
Le numéro séquentiel du membre de données de champ ou de paramètre est retourné dans ce paramètre. Ce nombre correspond à l’ordre du membre de données dans la fonction [CRecordset ::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [CRecordset ::D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération en cours peut être exécutée sur le champ ou le type de paramètre actuel.

### <a name="remarks"></a>Notes

Suivez le modèle des fonctions RFX existantes.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange :: SetFieldType

Vous avez besoin d’un appel à `SetFieldType` dans la substitution [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) de la classe Recordset.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Paramètres

*nFieldType*<br/>
Valeur de `enum FieldType` , déclarée dans `CFieldExchange` , qui peut être l’une des suivantes :

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Notes

Pour les membres de données de champ, vous devez appeler `SetFieldType` avec un paramètre de `CFieldExchange::outputColumn` , suivi d’appels aux fonctions RFX ou RFX en bloc. Si vous n’avez pas implémenté l’extraction de lignes en bloc, ClassWizard place cet `SetFieldType` appel pour vous dans la section mappage de champs de `DoFieldExchange` .

Si vous paramétrez votre classe de Recordset, vous devez appeler `SetFieldType` à nouveau, en dehors de toute section de mappage de champ, suivi d’appels RFX pour tous les membres de données de paramètre. Chaque type de membre de données de paramètre doit avoir son propre `SetFieldType` appel. Le tableau suivant distingue les différentes valeurs que vous pouvez passer à `SetFieldType` pour représenter les membres de données de paramètre de votre classe :

|Valeur du paramètre SetFieldType|Type de membre de données de paramètre|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Paramètre d’entrée. Valeur transmise dans la requête ou la procédure stockée de l’ensemble d’enregistrements.|
|`CFieldExchange::param` | identique à `CFieldExchange::inputParam` .|
|`CFieldExchange::outputParam`|Paramètre de sortie. Valeur de retour de la procédure stockée du Recordset.|
|`CFieldExchange::inoutParam`|Paramètre d’entrée/sortie. Valeur passée dans et retournée à partir de la procédure stockée du Recordset.|

En général, chaque groupe d’appels de fonction RFX associés à des données membres de champ ou de données de paramètre doit être précédé d’un appel à `SetFieldType` . Le paramètre *nFieldType* de chaque `SetFieldType` appel identifie le type des données membres représentées par les appels de fonction RFX qui suivent l' `SetFieldType` appel.

Pour plus d’informations sur la gestion des paramètres de sortie et d’entrée/sortie, consultez la `CRecordset` fonction membre [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Pour plus d’informations sur les fonctions RFX et RFX en bloc, consultez l’article [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

Cet exemple illustre plusieurs appels aux fonctions RFX avec des appels d’accompagnement à `SetFieldType` . Notez que `SetFieldType` est appelé par le biais du `pFX` pointeur vers un `CFieldExchange` objet.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
