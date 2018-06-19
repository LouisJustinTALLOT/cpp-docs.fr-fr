---
title: Implémente la Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ecbf0b77feef7abeb67f8d0dc300da067d1f2da
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880914"
---
# <a name="implements-structure"></a>Implements (structure)
Implémente QueryInterface et GetIid pour les interfaces spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `I0`  
 L’ID d’interface de zéro. (Obligatoire)  
  
 `I1`  
 Le premier ID d’interface. (facultatif)  
  
 `I2`  
 Le deuxième ID d’interface. (facultatif)  
  
 `I3`  
 L’ID d’interface tiers. (facultatif)  
  
 `I4`  
 La quatrième ID d’interface. (facultatif)  
  
 `I5`  
 La cinquième ID d’interface. (facultatif)  
  
 `I6`  
 La sixième ID d’interface. (facultatif)  
  
 `I7`  
 La septième ID d’interface. (facultatif)  
  
 `I8`  
 L’ID d’interface huitième. (facultatif)  
  
 `I9`  
 La neuvième ID d’interface. (facultatif)  
  
 `flags`  
 Indicateurs de configuration pour la classe. Un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérations qui sont spécifiées dans un [RuntimeClassFlags](../windows/runtimeclassflags-structure.md) structure.  
  
## <a name="remarks"></a>Notes  
 Dérive de la liste des interfaces spécifiées et implémente des modèles d’application d’assistance de QueryInterface et GetIid.  
  
 Chaque `I0` via `I9` paramètre d’interface doit dériver de l’interface IUnknown, IInspectable, ou [ChainInterfaces](../windows/chaininterfaces-structure.md) modèle. Le `flags` paramètre détermine si l’option prise en charge est générée pour IUnknown ou IInspectable.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`ClassFlags`|Synonyme de `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[Implements::CanCastTo, méthode](../windows/implements-cancastto-method.md)|Obtient un pointeur vers l’interface spécifiée.|  
|[Implements::CastToUnknown, méthode](../windows/implements-casttounknown-method.md)|Obtient un pointeur vers l’interface IUnknown sous-jacente.|  
|[Implements::FillArrayWithIid, méthode](../windows/implements-fillarraywithiid-method.md)|Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié.|  
  
### <a name="protected-constants"></a>Constantes protégés  
  
|Name|Description|  
|----------|-----------------|  
|[Implements::IidCount, constante](../windows/implements-iidcount-constant.md)|Contient le nombre d’ID d’interface implémentée.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)