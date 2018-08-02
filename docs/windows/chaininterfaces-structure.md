---
title: Chaininterfaces, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f16a10ef5119730fb492c4adb890aedcc09d3174
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461531"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces (structure)
Spécifie les fonctions de vérification et d'initialisation pouvant être appliquées à un ensemble d'ID d'interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *I0*  
 (Obligatoire) ID d’interface 0.  
  
 *I1*  
 (Obligatoire) ID d’interface 1.  
  
 *I2*  
 (Facultatif) ID d’interface 2.  
  
 *I3*  
 (Facultatif) ID d’interface 3.  
  
 *I4*  
 (Facultatif) ID d’interface 4.  
  
 *I5*  
 (Facultatif) ID d’interface 5.  
  
 *I6*  
 (Facultatif) ID d’interface 6.  
  
 *I7*  
 (Facultatif) ID d’interface 7.  
  
 *I8*  
 (Facultatif) ID d’interface 8.  
  
 *I9*  
 (Facultatif) ID d’interface 9.  
  
 *DerivedType*  
 Un type dérivé.  
  
 *BaseType*  
 Le type de base d’un type dérivé.  
  
 *hasImplements*  
 Une valeur booléenne qu’if **true**, signifie que vous ne pouvez pas utiliser un [MixIn](../windows/mixin-structure.md) structure avec une classe qui ne dérive pas de la [implémente](../windows/implements-structure.md) structure.  
  
## <a name="members"></a>Membres  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo, méthode](../windows/chaininterfaces-cancastto-method.md)|Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle ChainInterface.|  
|[ChainInterfaces::CastToUnknown, méthode](../windows/chaininterfaces-casttounknown-method.md)|Convertit le pointeur d’interface du type défini par le *I0* paramètre de modèle à un pointeur IUnknown.|  
|[ChainInterfaces::FillArrayWithIid, méthode](../windows/chaininterfaces-fillarraywithiid-method.md)|Stocke l’ID d’interface définie par le *I0* paramètre de modèle dans un emplacement spécifié dans un tableau spécifié d’ID d’interface.|  
|[ChainInterfaces::Verify, méthode](../windows/chaininterfaces-verify-method.md)|Vérifie que chaque interface définie par les paramètres de modèle *I0* via *I9* hérite `IUnknown` et/ou `IInspectable`et qui *I0* hérite de *I1* via *I9*.|  
  
### <a name="protected-constants"></a>Constantes protégés  
  
|Name|Description|  
|----------|-----------------|  
|[ChainInterfaces::IidCount, constante](../windows/chaininterfaces-iidcount-constant.md)|Le nombre total d’ID contenues dans les interfaces spécifiées par les paramètres de modèle d’interface *I0* via *I9*.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)