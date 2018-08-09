---
title: InterfaceTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6cb96b90a069c12e65c53158717d9a89fb0aed3d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014098"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<typename CloakedType>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
### <a name="parameters"></a>Paramètres  
 *I0*  
 Le nom d’une interface.  
  
 *CloakedType*  
 Pour `RuntimeClass`, `Implements` et `ChainInterfaces`, une interface qui ne sera pas dans la liste de prise en charge les ID d’interface.  
  
## <a name="remarks"></a>Notes  
 Caractéristiques communes d’implémente d’une interface.  
  
 Le deuxième modèle est une spécialisation pour les interfaces masqués. Le troisième modèle est une spécialisation pour les paramètres Nil.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`Base`|Un synonyme pour le *I0* paramètre de modèle.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo, méthode](../windows/interfacetraits-cancastto-method.md)|Indique si le pointeur spécifié peut être casté en un pointeur vers `Base`.|  
|[InterfaceTraits::CastToBase, méthode](../windows/interfacetraits-casttobase-method.md)|Effectue un cast du pointeur spécifié vers un pointeur vers `Base`.|  
|[InterfaceTraits::CastToUnknown, méthode](../windows/interfacetraits-casttounknown-method.md)|Effectue un cast du pointeur spécifié vers un pointeur vers `IUnknown`.|  
|[InterfaceTraits::FillArrayWithIid, méthode](../windows/interfacetraits-fillarraywithiid-method.md)|Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.|  
|[InterfaceTraits::Verify, méthode](../windows/interfacetraits-verify-method.md)|Vérifie que `Base` est dérivé correctement.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[InterfaceTraits::IidCount, constante](../windows/interfacetraits-iidcount-constant.md)|Contient le nombre d’ID associés en cours d’interface **InterfaceTraits** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `InterfaceTraits`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)