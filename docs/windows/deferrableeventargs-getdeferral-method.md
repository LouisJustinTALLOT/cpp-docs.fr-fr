---
title: DeferrableEventArgs::GetDeferral (méthode) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13cd6b361fccc49de6142a0640ff96dbab3cb92c
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571202"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral (méthode)
Obtient une référence à la [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet qui représente un événement différé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Résultat*  
 Un pointeur qui référence le [report](http://go.microsoft.com/fwlink/p/?linkid=526520) lors de la fin de l’appel de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple de code, consultez [deferrableeventargs, classe](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [DeferrableEventArgs, classe](../windows/deferrableeventargs-class.md)