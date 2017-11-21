---
title: ChainInterfaces (Structure) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces
dev_langs: C++
helpviewer_keywords: ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d48aac7e14092c8406db28910263e7048c17bee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
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
 `I0`  
 (Obligatoire) ID de l’interface 0.  
  
 `I1`  
 (Obligatoire) ID d’interface 1.  
  
 `I2`  
 (Facultatif) ID d’interface 2.  
  
 `I3`  
 (Facultatif) ID d’interface 3.  
  
 `I4`  
 (Facultatif) ID d’interface 4.  
  
 `I5`  
 (Facultatif) ID d’interface 5.  
  
 `I6`  
 (Facultatif) ID d’interface 6.  
  
 `I7`  
 (Facultatif) ID d’interface 7.  
  
 `I8`  
 (Facultatif) ID d’interface 8.  
  
 `I9`  
 (Facultatif) ID d’interface 9.  
  
 `DerivedType`  
 Un type dérivé.  
  
 `BaseType`  
 Le type de base d’un type dérivé.  
  
 `hasImplements`  
 Une valeur booléenne que se `true`, signifie que vous ne pouvez pas utiliser un [MixIn](../windows/mixin-structure.md) structure avec une classe qui ne dérive pas de la [implémente](../windows/implements-structure.md) structure.  
  
## <a name="members"></a>Membres  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo, méthode](../windows/chaininterfaces-cancastto-method.md)|Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle ChainInterface.|  
|[ChainInterfaces::CastToUnknown, méthode](../windows/chaininterfaces-casttounknown-method.md)|Convertit le pointeur d’interface du type défini par le `I0` paramètre de modèle à un pointeur vers IUnknown.|  
|[ChainInterfaces::FillArrayWithIid, méthode](../windows/chaininterfaces-fillarraywithiid-method.md)|Stocke l’ID d’interface défini par le `I0` paramètre de modèle dans un emplacement spécifié dans un tableau spécifié d’ID d’interface.|  
|[ChainInterfaces::Verify, méthode](../windows/chaininterfaces-verify-method.md)|Vérifie que chaque interface définie par les paramètres de modèle `I0` via `I9` hérite de IUnknown et/ou IInspectable et qui `I0` hérite `I1` via `I9`.|  
  
### <a name="protected-constants"></a>Constantes protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[ChainInterfaces::IidCount, constante](../windows/chaininterfaces-iidcount-constant.md)|Le nombre total d’ID contenus dans les interfaces spécifiées par les paramètres de modèle d’interface `I0` via `I9`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)