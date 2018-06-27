---
title: Classe de CFieldExchange | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96c70bc7c6c506d033b39ca55ba2b1a090767b5d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951685"
---
# <a name="cfieldexchange-class"></a>Classe de CFieldExchange
Prend en charge les routines d'échange de champs d'enregistrements (RFX) et d'échange de champs d'enregistrements en bloc (RFX en bloc) utilisées par les classes de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|Retourne zéro si l’opération en cours est approprié pour le type du champ mis à jour.|  
|[CFieldExchange::SetFieldType](#setfieldtype)|Spécifie le type de membre de données de jeu d’enregistrements, colonne ou du paramètre, représenté par tous les appels suivants à RFX (fonctions) jusqu'à ce que le prochain appel à `SetFieldType`.|  
  
## <a name="remarks"></a>Notes  
 `CFieldExchange` ne dispose pas d’une classe de base.  
  
 Utilisez cette classe si vous écrivez des routines d’échange de données pour les types de données personnalisés ou lorsque vous implémentez l’extraction de lignes en bloc ; dans le cas contraire, vous n’utiliserez pas directement cette classe. RFX et RFX en bloc échange des données entre les membres de données de champ de votre objet recordset et les champs correspondants de l’enregistrement actif sur la source de données.  
  
> [!NOTE]
>  Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt que les classes de base de données ODBC (Open Connectivity), utilisez la classe [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : base de données de programmation](../../data/data-access-programming-mfc-atl.md).  
  
 A `CFieldExchange` objet fournit les informations de contexte nécessitent pour RFX ou RFX en bloc en placez. `CFieldExchange` objets prennent en charge un nombre d’opérations, y compris les paramètres de liaison et les membres de données de champ et en définissant des indicateurs différents sur les champs de l’enregistrement actif. RFX et RFX en bloc des opérations sont effectuées sur les membres de données de classe de recordset de types définis par le **enum** **FieldType** dans `CFieldExchange`. Possible **FieldType** les valeurs sont :  
  
- **CFieldExchange::outputColumn** pour les membres de données de champ.  
  
- **CFieldExchange::inputParam** ou **CFieldExchange::param** pour les membres de données de paramètre d’entrée.  
  
- **CFieldExchange::outputParam** pour les membres de données de paramètre de sortie.  
  
- **CFieldExchange::inoutParam** pour les membres de données de paramètre d’entrée/sortie.  
  
 La plupart des membres de données et des fonctions de membre de la classe est fournie pour l’écriture de vos propres routines RFX personnalisés. Vous allez utiliser `SetFieldType` fréquemment. Pour plus d’informations, consultez les articles [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations sur les fonctions globales RFX et RFX en bloc, consultez [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md) dans la section MFC Macros and Globals de cette référence.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CFieldExchange`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdb.h  
  
##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType  
 Si vous écrivez votre propre fonction RFX, appelez `IsFieldType` au début de votre fonction pour déterminer si l’opération en cours peut être exécutée sur un type de membre données champ ou un paramètre particulier (une **CFieldExchange::outputColumn**, **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, ou **CFieldExchange::inoutParam** ).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnField*  
 Le numéro séquentiel du membre de données de champ ou un paramètre est retourné dans ce paramètre. Ce nombre correspond à l’ordre du membre de données dans le [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) (fonction).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération en cours peut être effectuée sur le type de champ ou un paramètre actuel.  
  
### <a name="remarks"></a>Notes  
 Suivre le modèle des fonctions RFX existants.  
  
##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType  
 Vous avez besoin d’un appel à `SetFieldType` dans votre classe de recordset [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) ou [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) remplacer.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Paramètres  
 *nFieldType*  
 Une valeur de la **enum FieldType**, déclarés dans `CFieldExchange`, ce qui peut prendre l’une des opérations suivantes :  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>Notes  
 Pour les membres de données de champ, vous devez appeler `SetFieldType` avec un paramètre de **CFieldExchange::outputColumn**, suivi d’appels de fonctions RFX et RFX en bloc. Si vous n’avez pas implémenté l’extraction de lignes en bloc, puis place ClassWizard `SetFieldType` appeler pour vous dans la section de mappage de champs de `DoFieldExchange`.  
  
 Si vous paramétrez votre classe de recordset, vous devez appeler `SetFieldType` à nouveau, en dehors d’une section de mappage de champ, suivi d’appels RFX pour tous les membres de données de paramètre. Chaque type de membre de données de paramètre doit avoir son propre `SetFieldType` appeler. Le tableau suivant fait la distinction les différentes valeurs que vous pouvez passer à `SetFieldType` pour représenter les membres de données de paramètre de la classe :  
  
|Valeur du paramètre SetFieldType|Type de membre de données de paramètre|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|Paramètre d’entrée. Une valeur qui a été passée dans la requête ou la procédure stockée du jeu d’enregistrements.|  
|**CFieldExchange::param**|Identique à **CFieldExchange::inputParam**.|  
|**CFieldExchange::outputParam**|Paramètre de sortie. Une valeur de retour de procédure stockée de jeu d’enregistrements.|  
|**CFieldExchange::inoutParam**|Paramètre d’entrée/sortie. Une valeur qui est passée et retournée à partir de l’ensemble d’enregistrements de procédure stockée.|  
  
 En général, chaque groupe d’appels de fonction RFX associé avec les membres de données de champ ou de membres de données de paramètre doit être précédé par un appel à `SetFieldType`. Le *nFieldType* de chaque paramètre de `SetFieldType` appel identifie le type des membres de données représenté par les appels de fonction RFX qui suivent le `SetFieldType` appeler.  
  
 Pour plus d’informations sur la gestion des paramètres de sortie et d’entrée/sortie, consultez le `CRecordset` fonction membre [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Pour plus d’informations sur les fonctions RFX et RFX en bloc, consultez la rubrique [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre plusieurs appels de fonctions RFX en termes d’appels à `SetFieldType`. Notez que `SetFieldType` est appelée via le `pFX` pointeur vers un `CFieldExchange` objet.  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CRecordset, classe](../../mfc/reference/crecordset-class.md)
