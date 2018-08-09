---
title: Weakref::as, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 938c7c796bf88d4ea1e49f1f59d274b5017aa7de
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649300"
---
# <a name="weakrefas-method"></a>WeakRef::As, méthode
Définit le texte spécifié `ComPtr` paramètre de pointeur pour représenter l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *U*  
 ID d’interface.  
  
 *ptr*  
 Lorsque cette opération se termine, un objet qui représente le paramètre *U*.  
  
## <a name="return-value"></a>Valeur de retour  
  
-   S_OK si cette opération réussit ; Sinon, un HRESULT qui indique la raison pour laquelle l’opération a échoué, et *ptr* a la valeur **nullptr**.  
  
-   S_OK si cette opération réussit, mais actuel **WeakRef** l’objet a déjà été libéré. Paramètre *ptr* a la valeur **nullptr**.  
  
-   S_OK si cette opération réussit, mais actuel **WeakRef** objet n’est pas dérivé de paramètre *U*. Paramètre *ptr* a la valeur **nullptr**.  
  
## <a name="remarks"></a>Notes  
 Une erreur est émise si le paramètre *U* est `IWeakReference`, ou n’est pas dérivé `IInspectable`.  
  
 Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../cpp/auto-cpp.md) .  
  
 À compter dans le SDK Windows 10, cette méthode n’affecte pas la **WeakRef** l’instance à **nullptr** si la référence faible n’a pas pu être obtenue, vous devez donc éviter le code de vérification des erreurs qui vérifie si weakref est pour **nullptr**. Au lieu de cela, vérifiez *ptr* pour **nullptr**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)