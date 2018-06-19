---
title: Weakref::CopyTo, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 817d984e995e7ac33ba80f978a282a8c0bac3e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890633"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo, méthode
Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `U`  
 Pointeur vers une interface IInspectable. Une erreur est générée si `U` n’est pas dérivé d’IInspectable.  
  
 `riid`  
 ID d’interface. Une erreur est générée si `riid` n’est pas dérivé d’ **IWeakReference**.  
  
 `ptr`  
 Pointeur doublement indirect vers IInspectable ou IWeakReference.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. Pour plus d'informations, consultez la section Notes.  
  
## <a name="remarks"></a>Notes  
 La valeur de retour S_OK signifie que cette opération a réussi, mais elle n’indique pas si la référence faible a été résolue en une référence forte. Si la valeur S_OK est retournée, tester que le paramètre `p` est une référence forte ; autrement dit que le paramètre `p` n’est pas égal à `nullptr`.  
  
 À compter du Kit de développement logiciel (SDK) Windows 10, cette méthode n’affecte pas la valeur `nullptr` à l’instance WeakRef si la référence faible n’a pas pu être obtenue. Vous devez donc éviter le code de vérification des erreurs qui vérifie si WeakRef est `nullptr`. Au lieu de cela, vérifiez `ptr` pour `nullptr`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)