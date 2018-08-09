---
title: Interfacetraits::cancastto, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2f8712e06838fb2d2269ba307a551997d7bd57c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018229"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *ptr*  
 Le nom d’un pointeur vers un type.  
  
 *riid*  
 L’ID d’interface de `Base`.  
  
 *PPV*  
 Si cette opération est réussie, *ppv* pointe vers l’interface spécifiée par `Base`. Sinon, *ppv* a la valeur **nullptr**.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si cette opération réussit et *ptr* est casté en un pointeur vers `Base`; sinon, **false** .  
  
## <a name="remarks"></a>Notes  
 Indique si le pointeur spécifié peut être casté en un pointeur vers `Base`.  
  
 Pour plus d’informations sur `Base`, consultez le **Typedefs publics** section [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)