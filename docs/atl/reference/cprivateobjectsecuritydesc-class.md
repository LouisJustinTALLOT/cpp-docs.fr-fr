---
title: Classe de CPrivateObjectSecurityDesc | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4845d652d2b1dceb8ffc0f2772f88565eb81e29
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="cprivateobjectsecuritydesc-class"></a>Classe de CPrivateObjectSecurityDesc
Cette classe représente un objet de descripteur de sécurité objet privé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Constructeur.|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) dans un format qui prend en charge la propagation automatique des entrées de contrôle d’accès pouvant être héritées (ACE).|  
|[CPrivateObjectSecurityDesc::Create](#create)|Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé en appelant le Gestionnaire des ressources.|  
|[CPrivateObjectSecurityDesc::Get](#get)|Appelez cette méthode pour récupérer les informations de descripteur de sécurité d’un objet privé.|  
|[CPrivateObjectSecurityDesc::Set](#set)|Appelez cette méthode pour modifier le descripteur de sécurité d’un objet privé.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Opérateur d'assignation.|  
  
## <a name="remarks"></a>Notes  
 Cette classe, dérivée de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), fournit des méthodes pour créer et gérer le descripteur de sécurité d’un objet privé.  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlsecurity.h  
  
##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) dans un format qui prend en charge la propagation automatique des entrées de contrôle d’accès pouvant être héritées (ACE).  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pParent`  
 Pointeur vers un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objet référençant le conteneur parent de l’objet. S’il n’existe aucun conteneur parent, ce paramètre est NULL.  
  
 `ObjectType`  
 Pointeur vers un **GUID** structure qui identifie le type d’objet associé à l’objet actuel. Définir `ObjectType` avec la valeur NULL si l’objet n’a pas un GUID.  
  
 `bIsDirectoryObject`  
 Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.  
  
 `GenericMapping`  
 Pointeur vers un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) structure qui spécifie le mappage de chaque droite générique à des droits spécifiques pour l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode tente de déterminer si les entrées dans le contrôle d’accès discrétionnaire (DACL) de liste et une liste de contrôle d’accès système (SACL) du descripteur de sécurité en cours ont été héritées à partir du descripteur de sécurité parent. Il appelle le [ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403) (fonction).  
  
##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 Constructeur.  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le `CPrivateObjectSecurityDesc` objet.  
  
##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc  
 Destructeur.  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Notes  
 Le destructeur libère toutes les ressources attribuées et supprime le descripteur de sécurité de l’objet privé.  
  
##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create  
 Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé en appelant le Gestionnaire des ressources.  
  
```
bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pParent`  
 Pointeur vers un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objet faisant référence au répertoire parent dans lequel un nouvel objet est en cours de création. La valeur NULL si aucun répertoire parent.  
  
 `pCreator`  
 Pointeur vers un descripteur de sécurité fourni par le créateur de l’objet. Si le créateur de l’objet ne passez pas explicitement les informations de sécurité pour le nouvel objet, ce paramètre la valeur NULL.  
  
 `bIsDirectoryObject`  
 Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.  
  
 `Token`  
 Référence à la [CAccessToken](../../atl/reference/caccesstoken-class.md) objet pour le processus client au nom duquel l’objet est créé.  
  
 `GenericMapping`  
 Pointeur vers un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) structure qui spécifie le mappage de chaque droite générique à des droits spécifiques pour l’objet.  
  
 `ObjectType`  
 Pointeur vers un **GUID** structure qui identifie le type d’objet associé à l’objet actuel. Définir `ObjectType` avec la valeur NULL si l’objet n’a pas un GUID.  
  
 *bIsContainerObject*  
 Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.  
  
 `AutoInheritFlags`  
 Un ensemble de bits indicateurs qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de `pParent`. Consultez [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405) ou [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581).  
  
 La seconde méthode permet en spécifiant le type d’objet GUID du nouvel objet ou de contrôler la façon dont les ACE sont héritées.  
  
> [!NOTE]
>  Un descripteur de sécurité auto-relatif est un descripteur de sécurité qui stocke toutes ses informations de sécurité dans un bloc contigu de mémoire.  
  
##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get  
 Appelez cette méthode pour récupérer les informations de descripteur de sécurité d’un objet privé.  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `si`  
 Un ensemble de bits indicateurs qui indiquent les parties du descripteur de sécurité à récupérer. Cette valeur peut être une combinaison de la [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bits indicateurs.  
  
 `pResult`  
 Pointeur vers un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objet qui reçoit une copie des informations demandées à partir du descripteur de sécurité spécifié.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Le descripteur de sécurité est une structure et les données associées qui contient les informations de sécurité pour un objet sécurisable.  
  
##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =  
 Opérateur d'assignation.  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rhs`  
 Le `CPrivateObjectSecurityDesc` objet à attribuer à l’objet actuel.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la mise à jour `CPrivateObjectSecurityDesc` objet.  
  
##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set  
 Appelez cette méthode pour modifier le descripteur de sécurité d’un objet privé.  
  
```
bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `si`  
 Un ensemble de bits indicateurs qui indiquent les parties du descripteur de sécurité à définir. Cette valeur peut être une combinaison de la [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bits indicateurs.  
  
 *Modification*  
 Pointeur vers un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objet. Les parties de ce descripteur de sécurité indiquaient par le `si` paramètre sont appliquées au descripteur de sécurité de l’objet.  
  
 `GenericMapping`  
 Pointeur vers un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) structure qui spécifie le mappage de chaque droite générique à des droits spécifiques pour l’objet.  
  
 `Token`  
 Référence à la [CAccessToken](../../atl/reference/caccesstoken-class.md) objet pour le processus client au nom duquel l’objet est créé.  
  
 `AutoInheritFlags`  
 Un ensemble de bits indicateurs qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de `pParent`. Consultez [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 La seconde méthode permet en spécifiant le type d’objet GUID de l’objet ou de contrôler la façon dont les ACE sont héritées.  
  
## <a name="see-also"></a>Voir aussi  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions de sécurité Global](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc, classe](../../atl/reference/csecuritydesc-class.md)
