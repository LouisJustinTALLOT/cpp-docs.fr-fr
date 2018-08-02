---
title: ActivateInstance (fonction) | Microsoft Docs
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
ms.openlocfilehash: 413bf73d5aeaef2c210be89f3c6f4ca3a4254ba4
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461969"
---
# <a name="activateinstance-function"></a>ActivateInstance (fonction)
Enregistre et récupère une instance d’un type spécifié défini dans un ID de classe spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Un type à activer.  
  
 *activatableClassId*  
 Le nom de l’ID de classe qui définit le paramètre *T*.  
  
 *Instance*  
 Lorsque cette opération se termine, une référence à une instance de *T*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Windows::Foundation  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)