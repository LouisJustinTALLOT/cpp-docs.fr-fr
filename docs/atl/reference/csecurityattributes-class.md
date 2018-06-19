---
title: Classe de CSecurityAttributes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs:
- C++
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03bda174fb85fa6857e22b851b93bcf1b3192716
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357504"
---
# <a name="csecurityattributes-class"></a>Classe de CSecurityAttributes
Cette classe est un wrapper mince pour la structure d’attributs de sécurité.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSecurityAttributes::Set](#set)|Appelez cette méthode pour définir les attributs de la `CSecurityAttributes` objet.|  
  
## <a name="remarks"></a>Notes  
 Le **SECURITY_ATTRIBUTES** structure contient un [descripteur de sécurité](http://msdn.microsoft.com/library/windows/desktop/aa379561) utilisé pour la création d’un objet et spécifie si le handle récupéré en spécifiant cette structure peut être hérité.  
  
 Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [le contrôle d’accès](http://msdn.microsoft.com/library/windows/desktop/aa374860) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes  
 Constructeur.  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSecurityDescriptor`  
 Référence à un descripteur de sécurité.  
  
 `bInheritsHandle`  
 Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.  
  
##  <a name="set"></a>  CSecurityAttributes::Set  
 Appelez cette méthode pour définir les attributs de la `CSecurityAttributes` objet.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `rSecurityDescriptor`  
 Référence à un descripteur de sécurité.  
  
 `bInheritHandle`  
 Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est utilisée par le constructeur pour initialiser le `CSecurityAttributes` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de sécurité](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [descripteur de sécurité](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
