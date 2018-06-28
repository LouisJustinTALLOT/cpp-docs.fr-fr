---
title: CLinearTransitionFromSpeed, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d6b3ba22fbe9feffc52d0f6ebfd970247929caa
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039480"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed, classe
Encapsule une transition de vitesse linéaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Construit un objet de transition de vitesse linéaire et l’initialise avec la vitesse et la valeur finale.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable à la fin de la transition de l’animation.|  
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|La valeur absolue de la rapidité de la variable.|  
  
## <a name="remarks"></a>Notes  
 Pendant une transition de vitesse linéaire, la valeur de la variable d’animation change à un taux spécifié. La durée de la transition est déterminée par la différence entre la valeur initiale et la valeur finale spécifiée. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed  
 Construit un objet de transition de vitesse linéaire et l’initialise avec la vitesse et la valeur finale.  
  
```  
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *dblSpeed*  
 La valeur absolue de la rapidité de la variable.  
  
 *dblFinalValue*  
 La valeur de la variable à la fin de la transition de l’animation.  
  
##  <a name="create"></a>  CLinearTransitionFromSpeed::Create  
 Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Paramètres  
*pLibrary*  
 Un pointeur vers un [interface IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), qui définit une bibliothèque de transitions standards.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la transition est créée avec succès ; Sinon, FALSE.  
  
##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue  
 La valeur de la variable à la fin de la transition de l’animation.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed  
 La valeur absolue de la rapidité de la variable.  
  
```  
DOUBLE m_dblSpeed;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
