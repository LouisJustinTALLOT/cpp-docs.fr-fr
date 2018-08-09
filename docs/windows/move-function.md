---
title: Move (fonction) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
dev_langs:
- C++
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 018b5832b187223484013702a1b7d4871d0b1d44
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015714"
---
# <a name="move-function"></a>Move (fonction)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<class T>  
inline typename RemoveReference<T>::Type&& Move(  
   _Inout_ T&& arg  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Type de l’argument.  
  
 *arg*  
 Un argument à déplacer.  
  
## <a name="return-value"></a>Valeur de retour  
 Paramètre *arg* après les caractéristiques de référence ou référence rvalue, le cas échéant, ont été supprimés.  
  
## <a name="remarks"></a>Notes  
 Déplace l’argument spécifié à partir d’un emplacement vers un autre.  
  
 Pour plus d’informations, consultez le **sémantique déplacer** section de [déclarateur de référence Rvalue : & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** internal.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)