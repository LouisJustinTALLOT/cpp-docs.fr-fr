---
title: Asweak, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a51b7095ec654c4ebb393c9a83d1e30fb52ce019
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462623"
---
# <a name="asweak-function"></a>AsWeak (fonction)
Récupère une référence faible à une instance spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Un pointeur vers le type de paramètre *p*.  
  
 *p*  
 Une instance d’un type.  
  
 *pWeak*  
 Lorsque cette opération se termine, un pointeur vers une référence faible au paramètre *p*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK, si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la cause de l’échec.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)