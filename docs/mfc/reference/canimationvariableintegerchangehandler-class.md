---
title: CAnimationVariableIntegerChangeHandler, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fae1d569f49a50d3b7281e86c72fd12c69b40832
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956357"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler, classe
Implémente un rappel, qui est appelé par l'API d'animation lorsque la valeur d'une variable de l'animation est modifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Construit un objet `CAnimationVariableIntegerChangeHandler`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Crée une instance de `CAnimationVariableIntegerChangeHandler` rappel.|  
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Appelée lorsqu’une valeur d’une variable d’animation a changé. (Substitue `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|  
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.|  
  
## <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements est créé et transmis à la méthode IUIAnimationVariable::SetVariableIntegerChangeHandler, lorsque vous appelez CAnimationVariable::EnableIntegerValueChangedEvent ou CAnimationBaseObject::EnableIntegerValueChangedEvent (ce qui permet Cet événement pour toutes les variables d’animation encapsulées dans un objet d’animation).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [Classes MFC](../../mfc/reference/mfc-classes.md)  
  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableIntegerChangeHandlerBase`  
  
 `CAnimationVariableIntegerChangeHandler`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="canimationvariableintegerchangehandler"></a>  CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler  
 Construit un objet CAnimationVariableIntegerChangeHandler.  
  
```  
CAnimationVariableIntegerChangeHandler ();
```  
  
##  <a name="createinstance"></a>  CAnimationVariableIntegerChangeHandler::CreateInstance  
 Crée une instance de rappel CAnimationVariableIntegerChangeHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```  
  
### <a name="parameters"></a>Paramètres  
 *pAnimationController*  
 Pointeur vers le contrôleur de l’animation, qui doit recevoir des événements.  
  
 *ppHandler*  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="onintegervaluechanged"></a>  CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged  
 Appelée lorsqu’une valeur d’une variable d’animation a changé.  
  
```  
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *table de montage séquentiel*  
 La table de montage séquentiel qui anime la variable.  
  
 *Variable*  
 La variable d’animation qui a été mis à jour.  
  
 *nouvelle valeur*  
 La nouvelle valeur arrondie.  
  
 *previousValue*  
 La précédente valeur arrondie.  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; sinon E_FAIL.  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableIntegerChangeHandler::SetAnimationController  
 Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Paramètres  
 *pAnimationController*  
 Pointeur vers le contrôleur de l’animation, qui doit recevoir des événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
