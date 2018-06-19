---
title: Handlet, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99a596bf1e086ac7b1a1a72c3504ce4f41844ba4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876148"
---
# <a name="handlet-class"></a>HandleT (classe)
Représente un handle d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `HandleTraits`  
 Une instance de la [HandleTraits](../windows/handletraits-structure.md) structure qui définit les caractéristiques communes d’un handle.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`Traits`|Synonyme de `HandleTraits`.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HandleT::HandleT, constructeur](../windows/handlet-handlet-constructor.md)|Initialise une nouvelle instance de la classe HandleT.|  
|[HandleT::~HandleT, destructeur](../windows/handlet-tilde-handlet-destructor.md)|Annule l’initialisation d’une instance de la classe HandleT.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[HandleT::Attach, méthode](../windows/handlet-attach-method.md)|Associe le handle spécifié à l’objet HandleT en cours.|  
|[HandleT::Close, méthode](../windows/handlet-close-method.md)|Ferme l’objet HandleT en cours.|  
|[HandleT::Detach, méthode](../windows/handlet-detach-method.md)|Dissocie l’objet HandleT actuel à partir de son handle sous-jacent.|  
|[HandleT::Get, méthode](../windows/handlet-get-method.md)|Obtient la valeur du handle sous-jacent.|  
|[HandleT::IsValid, méthode](../windows/handlet-isvalid-method.md)|Indique si l’objet HandleT actuel représente un handle.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[HandleT::InternalClose, méthode](../windows/handlet-internalclose-method.md)|Ferme l’objet HandleT en cours.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HandleT::operator=, opérateur](../windows/handlet-operator-assign-operator.md)|Déplace la valeur de l’objet HandleT spécifié à l’objet HandleT actuel.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[HandleT::handle_, données de membre](../windows/handlet-handle-data-member.md)|Contient le handle qui est représenté par l’objet HandleT.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HandleT`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)