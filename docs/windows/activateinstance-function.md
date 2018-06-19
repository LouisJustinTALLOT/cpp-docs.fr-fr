---
title: ActivateInstance (fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0bf945dd8225ca3c153d7f497ded6b83ebd022d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855573"
---
# <a name="activateinstance-function"></a>ActivateInstance (fonction)
Enregistre et récupère une instance d’un type spécifié défini dans un ID de classe spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Un type à activer.  
  
 `activatableClassId`  
 Le nom de l’ID de classe qui définit le paramètre `T`.  
  
 `instance`  
 Lorsque cette opération est terminée, une référence à une instance de `T`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Namespace :** Windows::Foundation  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)