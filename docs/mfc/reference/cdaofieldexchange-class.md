---
title: CDaoFieldExchange, classe | Microsoft Docs
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
ms.openlocfilehash: 9f5f4de25c0ed4643f93626f92a83942c70dfce5
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337838"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange, classe
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
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Spécifie le type de membre de données de jeu d’enregistrements, colonne ou du paramètre, représenté par tous les appels ultérieurs aux fonctions DFX jusqu’au prochain appel à `SetFieldType`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Section CDaoFieldExchange::m_nOperation](#m_noperation)|L’opération DFX en cours d’exécution par l’appel actuel à l’ensemble d’enregistrements `DoFieldExchange` fonction membre.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Pointeur vers le jeu d’enregistrements sur quel DFX opérations sont effectuées.|  
  
## <a name="remarks"></a>Notes  
 `CDaoFieldExchange` n’a pas d’une classe de base.  
  
 Utilisez cette classe si vous écrivez des routines d’échange de données pour les types de données personnalisés ; Sinon, vous pas directement utilise cette classe. DFX échange des données entre les membres de données de champ de votre [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet et les champs correspondants de l’enregistrement en cours sur la source de données. DFX gère l’échange dans les deux sens, à partir de la source de données et à la source de données. Consultez [53 de Note technique](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) pour plus d’informations sur l’écriture de routines DFX personnalisées.  
  
> [!NOTE]
>  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accès aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC. Les classes DAO peuvent accéder aux données, y compris via des pilotes ODBC, via leur propre moteur de base de données. Ils prennent également en charge les opérations de langage de définition de données (DDL), telles que l’ajout de tables via les classes au lieu de devoir appeler DAO vous-même.  
  
> [!NOTE]
>  Échange de champs d’enregistrements DAO (DFX) est très similaire à l’échange de champs d’enregistrements (RFX) dans les classes de base de données MFC basées sur ODBC ( `CDatabase`, `CRecordset`). Si vous comprenez RFX, vous trouverez DFX facile à utiliser.  
  
 Un `CDaoFieldExchange` objet fournit les informations de contexte nécessitent pour DAO enregistrer échange de champs pour prendre place. `CDaoFieldExchange` objets prennent en charge un nombre d’opérations, y compris les paramètres de liaison et les membres de données de champ et en définissant les différents indicateurs sur les champs de l’enregistrement en cours. Opérations DFX sont effectuées sur les membres de données de classe de recordset de types définis par le **enum** **FieldType** dans `CDaoFieldExchange`. Possible **FieldType** les valeurs sont :  
  
- `CDaoFieldExchange::outputColumn` pour les membres de données de champ.  
  
- `CDaoFieldExchange::param` pour les membres de données de paramètre.  
  
 Le [IsValidOperation](#isvalidoperation) fonction membre est fournie pour l’écriture de vos propres routines DFX personnalisées. Vous allez utiliser [SetFieldType](#setfieldtype) récurrents dans vos [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) fonctions. Pour plus d’informations sur les fonctions DFX globales, consultez [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md). Pour plus d’informations sur l’écriture des routines DFX personnalisées pour vos propres types de données, consultez [technique 53 Remarque](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 Si vous écrivez votre propre fonction DFX, appelez `IsValidOperation` au début de votre fonction pour déterminer si l’opération en cours peut être exécutée sur un type de membre de données de champ particulier (une `CDaoFieldExchange::outputColumn` ou `CDaoFieldExchange::param`).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération en cours est appropriée pour le type du champ mis à jour.  
  
### <a name="remarks"></a>Notes  
 Certaines des opérations effectuées par le mécanisme DFX s’appliquent uniquement à un des types de champ possibles. Suivez le modèle des fonctions DFX existants.  
  
 Pour plus d’informations sur l’écriture des routines DFX personnalisées, consultez [technique 53 Remarque](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>  Section CDaoFieldExchange::m_nOperation  
 Identifie l’opération à effectuer sur le [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet associé à l’objet exchange du champ.  
  
### <a name="remarks"></a>Notes  
 Le `CDaoFieldExchange` objet qui fournit le contexte pour un nombre d’opérations DFX différentes sur le jeu d’enregistrements.  
  
> [!NOTE]
>  La valeur PSEUDONULL décrite sous les opérations MarkForAddNew et SetFieldNull ci-dessous est une valeur utilisée pour marquer des champs de valeur Null. Le mécanisme d’échange de champs d’enregistrements (DFX) DAO utilise cette valeur pour déterminer les champs qui ont été explicitement marqués comme Null. PSEUDONULL n’est pas obligatoire pour [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) et [COleCurrency](../../mfc/reference/colecurrency-class.md) champs.  
  
 Les valeurs possibles de `m_nOperation` sont :  
  
|Opération|Description|  
|---------------|-----------------|  
|`AddToParameterList`|Génère le **paramètres** clause de l’instruction SQL.|  
|`AddToSelectList`|Génère le **sélectionnez** clause de l’instruction SQL.|  
|`BindField`|Lie un champ dans la base de données à un emplacement de mémoire dans votre application.|  
|`BindParam`|Définit les valeurs de paramètre pour la requête du recordset.|  
|`Fixup`|Définit l’état Null pour un champ.|  
|`AllocCache`|Alloue le cache utilisé pour rechercher les champs « modifiées » dans le jeu d’enregistrements.|  
|`StoreField`|Enregistre l’enregistrement actif dans le cache.|  
|`LoadField`|Restaure les variables de membre de données mises en cache dans le jeu d’enregistrements.|  
|`FreeCache`|Libère le cache utilisé pour rechercher les champs « modifiées » dans le jeu d’enregistrements.|  
|`SetFieldNull`|Définit l’état d’un champ sur Null et la valeur à PSEUDONULL.|  
|`MarkForAddNew`|Champs de marques « modifié » si pas PSEUDONULL.|  
|`MarkForEdit`|Marque les champs « modifiées » si elles ne correspondent pas le cache.|  
|`SetDirtyField`|Jeux de champ valeurs marquées comme « modifiées ».|  
|`DumpField`|Exporte le contenu d’un champ (debug uniquement).|  
|`MaxDFXOperation`|Utilisé pour la vérification des entrées.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 Contient un pointeur vers le [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet associé à la `CDaoFieldExchange` objet.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType  
 Appelez `SetFieldType` dans votre `CDaoRecordset` la classe `DoFieldExchange` remplacer.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Paramètres  
 *nFieldType*  
 Une valeur de la **enum FieldType**, déclarés dans `CDaoFieldExchange`, ce qui peut être une des opérations suivantes :  
  
- `CDaoFieldExchange::outputColumn`  
  
- `CDaoFieldExchange::param`  
  
### <a name="remarks"></a>Notes  
 Normalement, ClassWizard écrit cet appel pour vous. Si vous écrivez votre propre fonction et utilisez l’Assistant pour écrire votre `DoFieldExchange` fonctionne, ajoutez des appels à votre propre fonction à l’extérieur du mappage de champ. Si vous n’utilisez pas l’Assistant, il y aura pas un mappage de champ. L’appel précède les appels aux fonctions DFX, un pour chaque membre de données de champ de votre classe et identifie le type de champ en tant que `CDaoFieldExchange::outputColumn`.  
  
 Si vous paramétrez votre classe de jeu d’enregistrements, vous devez ajouter des appels DFX pour tous les membres de données de paramètre (à l’extérieur de la carte de champ) et faites précéder ces appels avec un appel à `SetFieldType`. Passez la valeur `CDaoFieldExchange::param`. (Vous pouvez, au lieu de cela, utilisez un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) et définir ses valeurs de paramètre.)  
  
 En règle générale, chaque groupe d’appels de fonctions DFX associé avec les membres de données de champ ou de membres de données de paramètre doit être précédé par un appel à `SetFieldType`. Le *nFieldType* paramètre de chaque `SetFieldType` appel identifie le type des membres de données représenté par les appels de fonction DFX qui suivent le `SetFieldType` appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)
