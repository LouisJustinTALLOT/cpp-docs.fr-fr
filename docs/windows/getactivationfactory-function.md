---
title: GetActivationFactory (fonction) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2cbb5be3603f79a7df1cb330ca06775357666854
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570309"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory (fonction)
Récupère une fabrique d’activation pour le type spécifié par le paramètre de modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Un paramètre de modèle qui spécifie le type de la fabrique d’activation.  
  
 *activatableClassId*  
 Le nom de la classe de la fabrique d’activation peut produire.  
  
 *fabrique*  
 Lorsque cette opération se termine, une référence à la fabrique d’activation pour le type *T*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Windows::Foundation  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)