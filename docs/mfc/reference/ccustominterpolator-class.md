---
title: CCustomInterpolator, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7ab45ad47ad0120fa4e04937e180841bdb5f981
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955087"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator, classe
Implémente un interpolateur de base.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Surchargé. Construit un objet de l’interpolateur personnalisé et initialise la durée et la rapidité des valeurs spécifiées.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur.|  
|[CCustomInterpolator::GetDuration](#getduration)|Obtient la durée de l’interpolateur.|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Obtient la valeur finale de l’interpolateur.|  
|[CCustomInterpolator::Init](#init)|Initialise la durée et la valeur finale.|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpole la valeur à un offset donné.|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpole la rapidité à un offset donné|  
|[CCustomInterpolator::SetDuration](#setduration)|Définit la durée de l’interpolateur.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur initiale et la rapidité de l’interpolateur.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|La valeur interpolée.|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Rapidité interpolée.|  
|[CCustomInterpolator::m_duration](#m_duration)|La durée de la transition.|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|La valeur finale d’une variable à la fin de la transition.|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|La valeur de la variable au début de la transition.|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|La rapidité de la variable au début de la transition.|  
  
## <a name="remarks"></a>Notes  
 Dérivez une classe de CCustomInterpolator et remplacez toutes les méthodes nécessaires pour implémenter un algorithme d’interpolation personnalisé. Un pointeur vers cette classe doit être passé en tant que paramètre à CCustomTransition.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator  
 Construit un objet de l’interpolateur personnalisé et définit toutes les valeurs par défaut 0.  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *Durée*  
 La durée de la transition.  
  
 *finalValue*  
  
### <a name="remarks"></a>Notes  
 Utilisez CCustomInterpolator::Init pour initialiser la durée et la valeur finale ultérieurement dans le code.  
  
##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies  
 Obtient les dépendances de l’interpolateur.  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Paramètres  
 *initialValueDependencies*  
 Sortie. Aspects de l’interpolateur qui dépendent de la valeur initiale transmise à SetInitialValueAndVelocity.  
  
 *initialVelocityDependencies*  
 Sortie. Aspects de l’interpolateur qui dépendent de la rapidité initiale transmise à SetInitialValueAndVelocity.  
  
 *durationDependencies*  
 Sortie. Aspects de l’interpolateur qui dépendent de la durée transmise à SetDuration.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="getduration"></a>  CCustomInterpolator::GetDuration  
 Obtient la durée de l’interpolateur.  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Paramètres  
 *Durée*  
 Sortie. La durée de la transition, en secondes.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue  
 Obtient la valeur finale de l’interpolateur.  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>Paramètres  
 *valeur*  
 Sortie. La valeur finale d’une variable à la fin de la transition.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="init"></a>  CCustomInterpolator::Init  
 Initialise la durée et la valeur finale.  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *Durée*  
 La durée de la transition.  
  
 *finalValue*  
 La valeur finale d’une variable à la fin de la transition.  
  
##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue  
 Interpole la valeur à un offset donné.  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>Paramètres  
 *valeur*  
 Sortie. La valeur interpolée.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity  
 Interpole la rapidité à un offset donné  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Paramètres  
 *rapidité*  
 Sortie. La rapidité de la variable à l’offset.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue  
 La valeur interpolée.  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="m_currentvelocity"></a>  CCustomInterpolator::m_currentVelocity  
 Rapidité interpolée.  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="m_duration"></a>  CCustomInterpolator::m_duration  
 La durée de la transition.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>  CCustomInterpolator::m_finalValue  
 La valeur finale d’une variable à la fin de la transition.  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>  CCustomInterpolator::m_initialValue  
 La valeur de la variable au début de la transition.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity  
 La rapidité de la variable au début de la transition.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>  CCustomInterpolator::SetDuration  
 Définit la durée de l’interpolateur.  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Paramètres  
 *Durée*  
 La durée de la transition.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity  
 Définit la valeur initiale et la rapidité de l’interpolateur.  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Paramètres  
 *initialValue*  
 La valeur de la variable au début de la transition.  
  
 *initialVelocity*  
 La rapidité de la variable au début de la transition.  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation renvoie toujours TRUE. Retourne FALSE de l’implémentation substituée si vous souhaitez que l’événement échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
