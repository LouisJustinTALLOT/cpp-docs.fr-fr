---
title: Weakref::weakref, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eafbddea6ae651d74d8f33be8efa58c25a8a0d3d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641471"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef, constructeur
Initialise une nouvelle instance de la **WeakRef** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *ptr*  
 Un pointeur, une référence ou une référence rvalue à un objet existant qui initialise actuel **WeakRef** objet.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise vide **WeakRef** objet. Le deuxième constructeur initialise un **WeakRef** objet d’un pointeur vers le `IWeakReference` interface. Le troisième constructeur initialise un **WeakRef** objet à partir d’une référence à un `ComPtr<IWeakReference>` objet. Les quatrième et cinquième constructeurs initialisent un **WeakRef** objet à partir d’un autre **WeakRef** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)