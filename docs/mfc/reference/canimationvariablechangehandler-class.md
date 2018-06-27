---
title: CAnimationVariableChangeHandler, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58646efaaa0087be2bd73e45acd8ade4a16e9767
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957089"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler, classe
Implémente un rappel, qui est appelé par l'API d'animation lorsque la valeur d'une variable de l'animation est modifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Construit un objet `CAnimationVariableChangeHandler`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|Crée une instance de `CAnimationVariableChangeHandler` objet.|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Appelée lorsqu’une valeur d’une variable d’animation a changé. (Substitue `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.|  
  
## <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements est créé et passé à `IUIAnimationVariable::SetVariableChangeHandler` méthode, lorsque vous appelez `CAnimationVariable::EnableValueChangedEvent` ou `CAnimationBaseObject::EnableValueChangedEvent` (ce qui permet à cet événement pour toutes les variables d’animation encapsulées dans un objet d’animation).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged  
 Appelée lorsqu’une valeur d’une variable d’animation a changé.  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *table de montage séquentiel*  
 La table de montage séquentiel qui anime la variable.  
  
 *Variable*  
 La variable d’animation qui a été mis à jour.  
  
 *nouvelle valeur*  
 Nouvelle valeur.  
  
 *previousValue*  
 La valeur précédente.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Paramètres  
 *pAnimationController*  
 Pointeur vers le contrôleur de l’animation, qui doit recevoir des événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
