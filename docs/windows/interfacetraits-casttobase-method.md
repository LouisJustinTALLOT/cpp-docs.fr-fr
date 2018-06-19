---
title: Interfacetraits::casttobase, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cd8fa2106ac3792c0352aa40ea34b049c1e5ce4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878523"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de paramètre `ptr`.  
  
 `ptr`  
 Pointeur vers un type `T`.  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers `Base`.  
  
## <a name="remarks"></a>Notes  
 Convertit le pointeur spécifié vers un pointeur vers `Base`.  
  
 Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [interfacetraits, Structure](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)