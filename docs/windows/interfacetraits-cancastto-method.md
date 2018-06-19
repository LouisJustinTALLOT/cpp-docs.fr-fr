---
title: Interfacetraits::cancastto, méthode | Documents Microsoft
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
ms.openlocfilehash: e2a0a37f4ef9fa8f2aa92405b4b2c01d99386555
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879579"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ptr`  
 Le nom d’un pointeur vers un type.  
  
 `riid`  
 L’ID d’interface de `Base`.  
  
 `ppv`  
 Si cette opération est réussie, `ppv` pointe vers l’interface spécifiée par `Base`. Dans le cas contraire, `ppv` a la valeur `nullptr`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si cette opération est réussie et `ptr` est casté en un pointeur vers `Base`; sinon, `false` .  
  
## <a name="remarks"></a>Notes  
 Indique si le pointeur spécifié peut être converti en un pointeur vers `Base`.  
  
 Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [interfacetraits, Structure](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)