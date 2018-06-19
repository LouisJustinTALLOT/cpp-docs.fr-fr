---
title: CAnimationSize, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1002ace78cf58c34c5e89bbafd81460ec5dabc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354133"
---
# <a name="canimationsize-class"></a>CAnimationSize, classe
Implémente les fonctionnalités d'un objet taille dont les dimensions peuvent être animées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|Surchargé. Construit un objet de taille de l’animation.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|Ajoute des transitions de largeur et de hauteur.|  
|[CAnimationSize::GetCX](#getcx)|Fournit l’accès à CAnimationVariable qui représente la largeur.|  
|[CAnimationSize::GetCY](#getcy)|Fournit l’accès à CAnimationVariable qui représente la hauteur.|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour la largeur et la hauteur.|  
|[CAnimationSize::GetValue](#getvalue)|Retourne la valeur actuelle.|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Insère les variables d’animation encapsulées dans une liste. (Substitue [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|Convertit CAnimationSize CSize.|  
|[CAnimationSize::operator =](#operator_eq)|Assigne szSrc à CAnimationSize.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|La variable d’animation encapsulée qui représente la largeur de la taille de l’animation.|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|La variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.|  
  
## <a name="remarks"></a>Notes  
 La classe CAnimationSize encapsule deux objets CAnimationVariable et peut représenter dans les applications une taille. Par exemple, vous pouvez utiliser cette classe pour animer une taille de n’importe quel objet bidimensionnel sur l’écran (comme un rectangle, contrôler etc.). Pour utiliser cette classe dans l’application, uniquement instancier un objet de cette classe, ajoutez-le au contrôleur de l’animation à l’aide de CAnimationController::AddAnimationObject et appeler AddTransition pour chaque transition à appliquer à la largeur ou hauteur.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationSize::AddTransition  
 Ajoute des transitions de largeur et de hauteur.  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCXTransition`  
 Pointeur vers la transition pour la largeur.  
  
 `pCYTransition`  
 Pointeur vers la transition pour la hauteur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour la largeur et la hauteur. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Transitions sont appliquées (ajoutée à une table de montage séquentiel pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à une des dimensions, vous pouvez passer NULL.  
  
##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize  
 Construit un objet de taille de l’animation.  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `szDefault`  
 Spécifie la taille par défaut.  
  
 `nGroupID`  
 Spécifie l’ID de groupe.  
  
 `nObjectID`  
 Spécifie l’ID d’objet.  
  
 `dwUserData`  
 Spécifie les données définies par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 L’objet est construit avec les valeurs par défaut pour la largeur, hauteur, ID d’objet et ID de groupe, qui sera défini à 0. Ils peuvent être modifiés ultérieurement lors de l’exécution avec SetDefaultValue et SetID.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList  
 Insère les variables d’animation encapsulées dans une liste.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Paramètres  
 `lst`  
 Lorsque la fonction est retournée, contient des pointeurs aux deux objets CAnimationVariable représentant la largeur et la hauteur.  
  
##  <a name="getcx"></a>  CAnimationSize::GetCX  
 Fournit l’accès à CAnimationVariable qui représente la largeur.  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à CAnimationVariable encapsulée qui représente la largeur.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez appeler cette méthode pour obtenir un accès direct à l’objet CAnimationVariable sous-jacent représentant la largeur.  
  
##  <a name="getcy"></a>  CAnimationSize::GetCY  
 Fournit l’accès à CAnimationVariable qui représente la hauteur.  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à CAnimationVariable encapsulée qui représente la hauteur.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez appeler cette méthode pour obtenir un accès direct à l’objet CAnimationVariable sous-jacent représentant la hauteur.  
  
##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue  
 Retourne les valeurs par défaut pour la largeur et la hauteur.  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un objet CSize contenant les valeurs par défaut.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour récupérer la valeur par défaut, ce qui a été définie précédemment par le constructeur ou SetDefaultValue.  
  
##  <a name="getvalue"></a>  CAnimationSize::GetValue  
 Retourne la valeur actuelle.  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>Paramètres  
 `szValue`  
 Sortie. Contient la valeur actuelle lorsque cette méthode est retournée.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la valeur actuelle a été correctement récupérée ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour extraire la valeur actuelle de la taille de l’animation. Si cette méthode échoue ou des objets COM sous-jacents pour la largeur et la taille n’ont pas été initialisés, szValue contient la valeur par défaut, ce qui a été définie précédemment dans le constructeur ou SetDefaultValue.  
  
##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue  
 La variable d’animation encapsulée qui représente la largeur de la taille de l’animation.  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue  
 La variable d’animation encapsulée qui représente la hauteur de la taille de l’animation.  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>  CAnimationSize::operator CSize  
 Convertit CAnimationSize CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle de la taille de l’animation CSize.  
  
### <a name="remarks"></a>Notes  
 Cette fonction a appelle GetValue en interne. Si GetValue échoue pour une raison quelconque, la taille retournée contient les valeurs par défaut pour la largeur et la hauteur.  
  
##  <a name="operator_eq"></a>  CAnimationSize::operator =  
 Assigne szSrc à CAnimationSize.  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `szSrc`  
 Fait référence à CSize ou SIZE.  
  
### <a name="remarks"></a>Notes  
 Assigne szSrc à CAnimationSize. Il est recommandé du pour faire avant le démarrage de l’animation, parce que cet opérateur appelle SetDefaultValue qui recrée les objets COM sous-jacents pour la largeur et la hauteur si elles ont été créées. Si vous êtes inscrit cet objet d’animation aux événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.  
  
##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue  
 Définit la valeur par défaut.  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 `szDefault`  
 Spécifie la nouvelle taille par défaut.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Ces méthodes assignent des valeurs par défaut pour la largeur et la hauteur de la taille de l’animation. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous êtes inscrit cet objet d’animation aux événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
