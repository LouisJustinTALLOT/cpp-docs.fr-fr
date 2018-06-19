---
title: Weakref::weakref, constructeur | Documents Microsoft
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
ms.openlocfilehash: ae70dabdd86fedf82c26c0c7d9a09d842e2310e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891046"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef, constructeur
Initialise une nouvelle instance de la classe WeakRef.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `ptr`  
 Un pointeur, une référence ou une référence rvalue à un objet existant qui initialise l’objet WeakRef actif.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un objet WeakRef vide. Le deuxième constructeur initialise un objet WeakRef à partir d’un pointeur vers l’interface IWeakReference. Le troisième constructeur initialise un objet WeakRef à partir d’une référence à un ComPtr\<IWeakReference > objet. Les quatrième et cinquième constructeurs initialise un objet WeakRef à partir d’un autre objet WeakRef.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)