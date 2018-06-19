---
title: WeakReference::setunknown, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28b25645b21d3101e2f2b2004f02f29482320808
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891013"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void SetUnknown(  
   _In_ IUnknown* unk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `unk`  
 Un pointeur vers le `IUnknown` interface d’un objet.  
  
## <a name="remarks"></a>Notes  
 Définit la référence forte actuelles `WeakReference` objet au pointeur d’interface spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi
[WeakReference (classe)](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)