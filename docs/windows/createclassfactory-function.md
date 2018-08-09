---
title: Createclassfactory, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57759e7191ecbe08e6d94dcec798f6d3203c13de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645137"
---
# <a name="createclassfactory-function"></a>CreateClassFactory (fonction)
Crée une fabrique produisant des instances de la classe spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *flags*  
 Une combinaison d’une ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valeurs d’énumération.  
  
 *entry*  
 Pointeur vers un [CreatorMap](../windows/creatormap-structure.md) qui contient des informations d’initialisation et d’inscription sur le paramètre *riid*.  
  
 *riid*  
 Référence à un ID d’interface.  
  
 *ppFactory*  
 Si cette opération termine avec succès, un pointeur vers une fabrique de classe.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="remarks"></a>Notes  
 Une erreur d’assertion est émise si le paramètre de modèle *Factory* n’est pas dérivé d’une interface `IClassFactory`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)