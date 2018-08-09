---
title: MakeAllocator (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 742b16dfc27e7e35a578bcc26283752c5c608012
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014154"
---
# <a name="makeallocator-class"></a>MakeAllocator (classe)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
 class MakeAllocator;  
  
template<typename T>  
class MakeAllocator<T, false>;  
  
template<typename T>  
class MakeAllocator<T, true>;  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Un nom de type.  
  
 *hasWeakReferenceSupport*  
 **true** d’allocation de mémoire pour un objet qui prend en charge les références faibles ; **false** d’allocation de mémoire pour un objet qui ne prend pas en charge les références faibles.  
  
## <a name="remarks"></a>Notes  
 Alloue la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.  
  
 Remplacer le **MakeAllocator** classe pour implémenter un modèle d’allocation de mémoire défini par l’utilisateur.  
  
 **MakeAllocator** est généralement utilisé pour empêcher les fuites de mémoire si un objet lève pendant la construction.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator, constructeur](../windows/makeallocator-makeallocator-constructor.md)|Initialise une nouvelle instance de la **MakeAllocator** classe.|  
|[MakeAllocator::~MakeAllocator, destructeur](../windows/makeallocator-tilde-makeallocator-destructor.md)|Annule l’initialisation de l’instance actuelle de la **MakeAllocator** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[MakeAllocator::Allocate, méthode](../windows/makeallocator-allocate-method.md)|Alloue de la mémoire et l’associe à actuel **MakeAllocator** objet.|  
|[MakeAllocator::Detach, méthode](../windows/makeallocator-detach-method.md)|Dissocie la mémoire allouée par le [Allocate](../windows/makeallocator-allocate-method.md) (méthode) à partir du **MakeAllocator** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `MakeAllocator`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)