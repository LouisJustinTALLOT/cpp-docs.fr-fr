---
title: CAnimationManagerEventHandler, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34ef63cf5c781348e873512c8b2f5bb190ae4976
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358256"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler, classe
Implémente un rappel, qui est appelé par l'API d'animation lorsque l'état d'un gestionnaire d'animation est modifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Construit un objet `CAnimationManagerEventHandler`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Crée une instance de `CAnimationManagerEventHandler` objet.|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Appelé lorsque l’état du Gestionnaire d’animations a modifié. (Substitue `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|  
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.|  
  
## <a name="remarks"></a>Notes  
 Ce gestionnaire d’événements est créé et passé à la méthode IUIAnimationManager::SetManagerEventHandler, lorsque vous appelez CAnimationController::EnableAnimationManagerEvent.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Construit un objet CAnimationManagerEventHandler.  
  
```  
CAnimationManagerEventHandler();
```  
  
##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Crée une instance de l’objet CAnimationManagerEventHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```  
  
### <a name="parameters"></a>Paramètres  
 `pAnimationController`  
 Pointeur vers le contrôleur de l’animation, qui doit recevoir des événements.  
  
 `ppManagerEventHandler`  
 Sortie. Si la méthode réussit, elle contient un pointeur vers un objet COM qui va gérer les mises à jour de l’état à un gestionnaire d’animation.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Appelé lorsque l’état du Gestionnaire d’animations a modifié.  
  
```  
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Paramètres  
 `newStatus`  
 Nouvel état.  
  
 `previousStatus`  
 État précédent.  
  
### <a name="return-value"></a>Valeur de retour  
 Implémentation actuelle retourne toujours S_OK ;  
  
##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Paramètres  
 `pAnimationController`  
 Pointeur vers le contrôleur de l’animation, qui doit recevoir des événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
