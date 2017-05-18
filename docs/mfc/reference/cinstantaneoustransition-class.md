---
title: Classe CInstantaneousTransition | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
dev_langs:
- C++
helpviewer_keywords:
- CInstantaneousTransition class
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: d0d6d4bee051222bec4333f486f493c2feeda9d6
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition, classe
Encapsule une transition instantanée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Construit un objet de transition et initialise sa valeur finale.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CInstantaneousTransition::Create](#create)|Appelle la bibliothèque des transitions pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable d’animation à la fin de la transition.|  
  
## <a name="remarks"></a>Remarques  
 Pendant une transition instantanée, la valeur de la variable d’animation change instantanément à partir de sa valeur actuelle à une valeur finale spécifiée. La durée de cette transition est toujours zéro. Car toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouveau opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que c’est NULL. Modification des variables de membre après que la création de cet objet COM n’a aucun effet.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="cinstantaneoustransition"></a>CInstantaneousTransition::CInstantaneousTransition  
 Construit un objet de transition et initialise sa valeur finale.  
  
```  
CInstantaneousTransition(DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Paramètres  
 `dblFinalValue`  
 La valeur de la variable d’animation à la fin de la transition.  
  
##  <a name="create"></a>CInstantaneousTransition::Create  
 Appelle la bibliothèque des transitions pour créer l’objet COM de transition encapsulé.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Paramètres  
`pLibrary`  
 Un pointeur vers un [interface IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), qui définit une bibliothèque de transitions standards.  

  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la transition est créée avec succès ; Sinon, FALSE.  
  
##  <a name="m_dblfinalvalue"></a>CInstantaneousTransition::m_dblFinalValue  
 La valeur de la variable d’animation à la fin de la transition.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)

