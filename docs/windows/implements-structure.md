---
title: Implémente la Structure | Microsoft Docs
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
ms.openlocfilehash: 0dc23a9c90fc2112d67180ceae86ebde0e057b06
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607804"
---
# <a name="implements-structure"></a>Implements (structure)
Implémente `QueryInterface` et `GetIid` pour les interfaces spécifiées.  
  
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
  
### <a name="parameters"></a>Paramètres  
 *I0*  
 L’ID d’interface de zéro. (Obligatoire)  
  
 *I1*  
 Le premier ID d’interface. (facultatif)  
  
 *I2*  
 Le deuxième ID d’interface. (facultatif)  
  
 *I3*  
 Le troisième ID d’interface. (facultatif)  
  
 *I4*  
 La quatrième ID d’interface. (facultatif)  
  
 *I5*  
 Le cinquième ID d’interface. (facultatif)  
  
 *I6*  
 Le sixième ID d’interface. (facultatif)  
  
 *I7*  
 Le septième ID d’interface. (facultatif)  
  
 *I8*  
 L’ID d’interface huitième. (facultatif)  
  
 *I9*  
 Le neuvième ID d’interface. (facultatif)  
  
 *flags*  
 Indicateurs de configuration pour la classe. Un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérations qui sont spécifiées dans un [RuntimeClassFlags](../windows/runtimeclassflags-structure.md) structure.  
  
## <a name="remarks"></a>Notes  
 Dérive de la liste des interfaces spécifiées et implémente des modèles d’assistance pour `QueryInterface` et `GetIid`.  
  
 Chaque *I0* via *I9* paramètre d’interface doit être dérivé `IUnknown`, `IInspectable`, ou le [ChainInterfaces](../windows/chaininterfaces-structure.md) modèle. Le *indicateurs* paramètre détermine si la prise en charge est généré pour `IUnknown` ou `IInspectable`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`ClassFlags`|Synonyme de `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[Implements::CanCastTo, méthode](../windows/implements-cancastto-method.md)|Obtient un pointeur vers l’interface spécifiée.|  
|[Implements::CastToUnknown, méthode](../windows/implements-casttounknown-method.md)|Obtient un pointeur vers sous-jacent `IUnknown` interface.|  
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)