---
title: Implements::cancastto, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a73aac6fb36270f0cd04615d9e530b29841850f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010920"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo, méthode
Obtient un pointeur vers l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *riid*  
 Une référence à un ID d’interface.  
  
 *PPV*  
 Si réussie, un pointeur vers l’interface spécifiée par *riid*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, un HRESULT qui indique l’erreur, telles que E_NOINTERFACE.  
  
## <a name="remarks"></a>Notes  
 Il s’agit d’une fonction d’assistance interne qui exécute une opération de QueryInterface.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Implements, structure](../windows/implements-structure.md)