---
title: Classe d’objet CDaoFieldExchange | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9e65b4880c80f8a4b0d9a192f316b16a92a3e69
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953907"
---
# <a name="cdaofieldexchange-class"></a>Classe d’objet CDaoFieldExchange
Prend en charge les routines d'échange de champs d'enregistrements DAO (DFX) utilisées par les classes de base de données DAO.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Retourne zéro si l’opération en cours est approprié pour le type du champ mis à jour.|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Spécifie le type de membre de données de jeu d’enregistrements, colonne ou du paramètre, représenté par tous les appels aux fonctions DFX jusqu’au prochain appel à `SetFieldType`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Section CDaoFieldExchange::m_nOperation](#m_noperation)|L’opération DFX en cours d’exécution par l’appel à l’ensemble d’enregistrements `DoFieldExchange` fonction membre.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Pointeur vers le jeu d’enregistrements sur quel DFX opérations sont effectuées.|  
  
## <a name="remarks"></a>Notes  
 `CDaoFieldExchange` ne dispose pas d’une classe de base.  
  
 Utilisez cette classe si vous écrivez des routines d’échange de données pour les types de données personnalisés ; dans le cas contraire, vous n’utiliserez pas directement cette classe. DFX échange des données entre les membres de données de champ de votre [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet et les champs correspondants de l’enregistrement actif sur la source de données. DFX gère l’échange dans les deux sens, à partir de la source de données et à la source de données. Consultez [53 de Note technique](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) pour plus d’informations sur l’écriture des routines DFX personnalisées.  
  
> [!NOTE]
>  Les classes de base de données DAO sont distincts des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accès aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC. Les classes DAO peuvent accéder aux données, y compris par le biais des pilotes ODBC, via leur propre moteur de base de données. Ils prennent également en charge les opérations de langage de définition de données (DDL), telles que l’ajout de tables via les classes au lieu de devoir appeler DAO vous-même.  
  
> [!NOTE]
>  Échange de champs d’enregistrements DAO (DFX) est très similaire à l’échange de champs d’enregistrements (RFX) dans les classes de base de données basées sur ODBC de MFC ( `CDatabase`, `CRecordset`). Si vous connaissez RFX, vous trouverez DFX facile à utiliser.  
  
 A `CDaoFieldExchange` objet fournit les informations de contexte nécessitent pour DAO enregistrer échange de champs doit avoir lieu. `CDaoFieldExchange` objets prennent en charge un nombre d’opérations, y compris les paramètres de liaison et les membres de données de champ et en définissant des indicateurs différents sur les champs de l’enregistrement actif. Opérations DFX sont effectuées sur les membres de données de classe de recordset des types définis par le **enum** **FieldType** dans `CDaoFieldExchange`. Possible **FieldType** les valeurs sont :  
  
- **CDaoFieldExchange::outputColumn** pour les membres de données de champ.  
  
- **CDaoFieldExchange::param** pour les membres de données de paramètre.  
  
 Le [IsValidOperation](#isvalidoperation) fonction membre est fournie pour l’écriture de vos propres routines DFX personnalisées. Vous allez utiliser [SetFieldType](#setfieldtype) fréquemment dans votre [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) fonctions. Pour plus d’informations sur les fonctions DFX globales, consultez [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’écriture des routines DFX personnalisées pour vos propres types de données, consultez [Technical Note 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 Si vous écrivez votre propre fonction DFX, appelez `IsValidOperation` au début de votre fonction pour déterminer si l’opération en cours peut être exécutée sur un type de membre de données de champ particulier (une **CDaoFieldExchange::outputColumn** ou un **CDaoFieldExchange::param**).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération en cours est appropriée pour le type du champ mis à jour.  
  
### <a name="remarks"></a>Notes  
 Certains des opérations effectuées par le mécanisme DFX s’appliquent uniquement à l’un des types de champ possibles. Suivre le modèle des fonctions DFX existants.  
  
 Pour plus d’informations sur l’écriture des routines DFX personnalisées, consultez [Technical Note 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>  Section CDaoFieldExchange::m_nOperation  
 Identifie l’opération à effectuer sur le [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet associé à l’objet exchange de champ.  
  
### <a name="remarks"></a>Notes  
 Le `CDaoFieldExchange` objet qui fournit le contexte pour un nombre d’opérations DFX différentes sur le jeu d’enregistrements.  
  
> [!NOTE]
>  Le **PSEUDONULL** valeur décrite dans les opérations MarkForAddNew et SetFieldNull ci-dessous est une valeur utilisée pour marquer des champs Null. Le mécanisme d’échange champs d’enregistrements DAO (DFX) utilise cette valeur pour déterminer les champs qui ont été marqués explicitement Null. **PSEUDONULL** n’est pas requis pour [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) et [COleCurrency](../../mfc/reference/colecurrency-class.md) champs.  
  
 Les valeurs possibles de **m_nOperation** sont :  
  
|Opération|Description|  
|---------------|-----------------|  
|**AddToParameterList**|Génère le **paramètres** clause de l’instruction SQL.|  
|**AddToSelectList**|Génère le **sélectionnez** clause de l’instruction SQL.|  
|**BindField**|Lie un champ dans la base de données à un emplacement de mémoire dans votre application.|  
|**BindParam**|Définit les valeurs de paramètre pour la requête du recordset.|  
|**Correction**|Définit l’état Null pour un champ.|  
|**AllocCache**|Alloue le cache utilisé pour vérifier les champs « modifiées » dans le jeu d’enregistrements.|  
|**StoreField**|Enregistre l’enregistrement actif dans le cache.|  
|**LoadField**|Restaure les variables de membre de données mises en cache dans le jeu d’enregistrements.|  
|**FreeCache**|Libère le cache utilisé pour vérifier les champs « modifiées » dans le jeu d’enregistrements.|  
|**SetFieldNull**|Définit l’état d’un champ Null et la valeur **PSEUDONULL**.|  
|**MarkForAddNew**|Marque les champs « modifiées » dans le cas contraire **PSEUDONULL**.|  
|**MarkForEdit**|Marque les champs « modifiées » si elles ne correspondent pas le cache.|  
|**SetDirtyField**|Jeux de champ valeurs marqués comme « modifiées ».|  
|**DumpField**|Vide le contenu d’un champ (debug uniquement).|  
|**MaxDFXOperation**|Utilisé pour un contrôle d’entrée.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 Contient un pointeur vers le [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet associé à la `CDaoFieldExchange` objet.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType  
 Appelez `SetFieldType` dans votre `CDaoRecordset` de classe `DoFieldExchange` remplacer.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Paramètres  
 *nFieldType*  
 Une valeur de la **enum FieldType**, déclarés dans `CDaoFieldExchange`, ce qui peut être une des opérations suivantes :  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>Notes  
 Normalement, ClassWizard écrit cet appel pour vous. Si vous écrivez votre propre fonction et utilisez l’Assistant pour écrire votre `DoFieldExchange` fonctionne, ajoutez des appels à votre propre fonction à l’extérieur du mappage de champs. Si vous n’utilisez pas l’Assistant, il y aura pas un mappage de champ. L’appel précède les appels aux fonctions DFX, un pour chaque membre de données de champ de votre classe et identifie le type de champ en tant que `CDaoFieldExchange::outputColumn`.  
  
 Si vous paramétrez votre classe de recordset, vous devez ajouter des appels DFX pour tous les membres de données de paramètre (à l’extérieur du mappage de champs) et faites précéder ces appels avec un appel à `SetFieldType`. Passez la valeur `CDaoFieldExchange::param`. (Vous pouvez utiliser à la place, un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et définir ses valeurs de paramètre.)  
  
 En général, chaque groupe d’appels de fonction DFX associé avec les membres de données de champ ou de membres de données de paramètre doit être précédé par un appel à `SetFieldType`. Le `nFieldType` de chaque paramètre de `SetFieldType` appel identifie le type des membres de données représenté par les appels de fonction DFX qui suivent le `SetFieldType` appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)
