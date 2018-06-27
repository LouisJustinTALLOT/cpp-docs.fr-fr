---
title: CAnimationValue, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b762c3abb5f57574dc2a60d6b2145af2e0c0484b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952096"
---
# <a name="canimationvalue-class"></a>CAnimationValue, classe
Implémente les fonctionnalités d'un objet d'animation qui a une valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationValue::CAnimationValue](#canimationvalue)|Surchargé. Construit un objet CAnimationValue.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationValue::AddTransition](#addtransition)|Ajoute une transition à appliquer à une valeur.|  
|[CAnimationValue::GetValue](#getvalue)|Surchargé. Récupère la valeur actuelle.|  
|[CAnimationValue::GetVariable](#getvariable)|Fournit l’accès à la variable d’animation encapsulée.|  
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Place la variable d’animation encapsulée dans une liste. (Substitue [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationValue::operator DOUBLE](#operator_double)|Fournit la conversion entre CAnimationValue et DOUBLE.|  
|[CAnimationValue::operator INT32](#operator_int32)|Fournit la conversion entre CAnimationValue et INT32.|  
|[CAnimationValue::operator =](#operator_eq)|Surchargé. Affecte une valeur INT32 à CAnimationValue.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAnimationValue::m_value](#m_value)|La variable d’animation encapsulée qui représente la valeur de l’animation.|  
  
## <a name="remarks"></a>Notes  
 La classe CAnimationValue encapsule un objet CAnimationVariable unique et peut représenter dans les applications une valeur animée unique. Par exemple, vous pouvez utiliser cette classe pour la transparence animée (effet d’atténuation), l’angle (faire pour pivoter des objets), ou pour tous les autres cas lorsque vous avez besoin créer une animation en fonction d’une valeur animée unique. Pour utiliser cette classe dans l’application, uniquement instancier un objet de cette classe, ajoutez-le au contrôleur de l’animation à l’aide de CAnimationController::AddAnimationObject et appeler AddTransition pour chaque transition à appliquer à la valeur.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationValue`
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationValue::AddTransition  
 Ajoute une transition à appliquer à une valeur.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Paramètres  
 *pTransition*  
 Pointeur vers un objet de transition.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour ajouter une transition à une liste interne des transitions à appliquer à une variable de l’animation. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Transitions sont appliquées (ajoutée à une table de montage séquentiel pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup.  
  
##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue  
 Construit un objet CAnimationValue.  
  
```  
CAnimationValue();

 
CAnimationValue(
    DOUBLE dblDefaultValue,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *dblDefaultValue*  
 Spécifie la valeur par défaut.  
  
 *nGroupID*  
 Spécifie l’ID de groupe.  
  
 *nObjectID*  
 Spécifie l’ID d’objet.  
  
 *dwUserData*  
 Spécifie les données définies par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Construit un objet CAnimationValue avec les propriétés par défaut : valeur par défaut, ID de groupe et l’ID d’objet sont définies sur 0.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList  
 Place la variable d’animation encapsulée dans une liste.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Paramètres  
 *lst*  
 Lorsque la fonction est retournée, elle contient un pointeur à CAnimationVariable qui représente la valeur animée.  
  
##  <a name="getvalue"></a>  CAnimationValue::GetValue  
 Récupère la valeur actuelle.  
  
```  
BOOL GetValue(DOUBLE& dblValue);  
BOOL GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *dblValue*  
 Sortie. Lorsque la fonction retourne, elle contient une valeur actuelle de la variable de l’animation.  
  
 *nValeur*  
 Sortie. Lorsque la fonction retourne, elle contient une valeur actuelle de la variable de l’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour extraire la valeur actuelle. Cette implémentation appelle l’objet COM encapsulé, et si l’appel échoue, cette méthode retourne la valeur par défaut qui a été définie précédemment dans le constructeur ou avec SetDefaultValue.  
  
##  <a name="getvariable"></a>  CAnimationValue::GetVariable  
 Fournit l’accès à la variable d’animation encapsulée.  
  
```  
CAnimationVariable& GetVariable();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la variable d’animation encapsulée.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour accéder à la variable d’animation encapsulée. À partir de CAnimationVariable, vous pouvez accéder à l’objet IUIAnimationVariable sous-jacent dont le pointeur peut être NULL si la variable d’animation n’a pas été créé.  
  
##  <a name="m_value"></a>  CAnimationValue::m_value  
 La variable d’animation encapsulée qui représente la valeur de l’animation.  
  
```  
CAnimationVariable m_value;  
```  
  
##  <a name="operator_double"></a>  CAnimationValue::operator DOUBLE  
 Fournit la conversion entre CAnimationValue et DOUBLE.  
  
```  
operator DOUBLE();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle de la valeur de l’Animation.  
  
### <a name="remarks"></a>Notes  
 Fournit la conversion entre CAnimationValue et DOUBLE. Cette méthode appelle GetValue en interne et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contient une valeur par défaut définie précédemment dans le constructeur ou avec SetDefaultValue.  
  
##  <a name="operator_int32"></a>  CAnimationValue::operator INT32  
 Fournit la conversion entre CAnimationValue et INT32.  
  
```  
operator INT32();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle de la valeur de l’Animation en tant qu’entier.  
  
### <a name="remarks"></a>Notes  
 Fournit la conversion entre CAnimationValue et INT32. Cette méthode appelle GetValue en interne et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contient une valeur par défaut définie précédemment dans le constructeur ou avec SetDefaultValue.  
  
##  <a name="operator_eq"></a>  CAnimationValue::operator =  
 Assigne une valeur DOUBLE à CAnimationValue.  
  
```  
void operator=(DOUBLE dblVal);  
void operator=(INT32 nVal);
```  
  
### <a name="parameters"></a>Paramètres  
 *dblVal*  
 Spécifie la valeur à affecter à la valeur de l’Animation.  
  
 *nVal*  
 Spécifie la valeur à affecter à la valeur de l’Animation.  
  
### <a name="remarks"></a>Notes  
 Assigne une valeur DOUBLE à CAnimationValue. Cette valeur est définie comme valeur par défaut pour la variable d’animation encapsulée. Si vous êtes inscrit cet objet d’animation aux événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.  
  
##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue  
 Définit la valeur par défaut.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *dblDefaultValue*  
 Spécifie la valeur par défaut.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir une valeur par défaut. Une valeur par défaut est retournée à l’application lors de l’animation n’a pas été démarrée et/ou l’objet COM sous-jacent n’a pas été créé. Si l’objet COM sous-jacent encapsulé dans CAnimationVarible a déjà été créé, cette méthode recrée, par conséquent, vous devrez appeler les méthodes EnableValueChanged/EnableIntegerValueChanged de nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
