---
title: Classe de CHandle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b57aab927380f8801c3b9cab258a695c7d8a59d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363069"
---
# <a name="chandle-class"></a>Classe de CHandle
Cette classe fournit des méthodes pour la création et à l’aide d’un handle d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CHandle
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|Constructeur.|  
|[CHandle :: ~ CHandle](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|Appelez cette méthode pour attacher le `CHandle` objet à un handle existant.|  
|[CHandle::Close](#close)|Appelez cette méthode pour fermer une `CHandle` objet.|  
|[CHandle::Detach](#detach)|Appelez cette méthode pour détacher un handle d’un `CHandle` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHandle::operator descripteur](#operator_handle)|Retourne la valeur du handle stockée.|  
|[CHandle::operator =](#operator_eq)|Opérateur d'assignation.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|La variable de membre qui stocke le descripteur.|  
  
## <a name="remarks"></a>Notes  
 A `CHandle` objet peut être utilisé chaque fois qu’un handle est requis : la principale différence est que le `CHandle` objet sera automatiquement supprimé.  
  
> [!NOTE]
>  Certaines fonctions API utilisera NULL comme un handle non valide ou vide, alors que d’autres utilisent INVALID_HANDLE_VALUE. `CHandle` utilise NULL et ne traitez INVALID_HANDLE_VALUE comme un handle réel. Si vous appelez une API qui peut retourner INVALID_HANDLE_VALUE, vous devez rechercher cette valeur avant d’appeler [CHandle::Attach](#attach) ou en le passant à la `CHandle` constructeur et passer à la place la valeur NULL.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="attach"></a>  CHandle::Attach  
 Appelez cette méthode pour attacher le `CHandle` objet à un handle existant.  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `h`  
 `CHandle` prend possession du handle `h`.  
  
### <a name="remarks"></a>Notes  
 Affecte le `CHandle` de l’objet à le `h` gérer. Dans les versions débogue un ATLASSERT ; sera déclenchée si `h` a la valeur NULL. Aucune autre vérification sur la validité de la poignée est effectuée.  
  
##  <a name="chandle"></a>  CHandle::CHandle  
 Constructeur.  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `h`  
 Un handle existant ou `CHandle`.  
  
### <a name="remarks"></a>Notes  
 Crée un nouveau `CHandle` de l’objet, si vous le souhaitez à l’aide d’un handle existant ou `CHandle` objet.  
  
##  <a name="dtor"></a>  CHandle :: ~ CHandle  
 Destructeur.  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère le `CHandle` objet en appelant [CHandle::Close](#close).  
  
##  <a name="close"></a>  CHandle::Close  
 Appelez cette méthode pour fermer une `CHandle` objet.  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>Notes  
 Ferme le handle d’objet ouvert. Si le handle est NULL, ce qui sera le cas si **fermer** a déjà été appelée, une ATLASSERT ; sera déclenchée dans les versions debug.  
  
##  <a name="detach"></a>  CHandle::Detach  
 Appelez cette méthode pour détacher un handle d’un `CHandle` objet.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le handle qui est détaché.  
  
### <a name="remarks"></a>Notes  
 Libère la possession de la poignée.  
  
##  <a name="m_h"></a>  CHandle::m_h  
 La variable de membre qui stocke le descripteur.  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>  CHandle::operator =  
 L’opérateur d’assignation.  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `h`  
 `CHandle` prend possession du handle `h`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à la nouvelle `CHandle` objet.  
  
### <a name="remarks"></a>Notes  
 Si le `CHandle` objet contient actuellement un handle, il va être fermée. Le `CHandle` de l’objet en cours de passage aura sa référence de descripteur de la valeur NULL. Cela garantit que deux `CHandle` objets ne contient jamais le même handle actif.  
  
##  <a name="operator_handle"></a>  CHandle::operator descripteur  
 Retourne la valeur du handle stockée.  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne la valeur stockée dans [CHandle::m_h](#m_h).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
