---
title: GetActivationFactory (fonction) | Documents Microsoft
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
ms.openlocfilehash: f1a4bf31ff44c74362e21e8888630273fcc049e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881336"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory (fonction)
Récupère la fabrique d’activation pour le type spécifié par le paramètre de modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Un paramètre de modèle qui spécifie le type de la fabrique d’activation.  
  
 `activatableClassId`  
 Le nom de la classe qui permet de créer la fabrique d’activation.  
  
 `factory`  
 Lorsque cette opération est terminée, une référence à la fabrique d’activation pour le type `T`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Namespace :** Windows::Foundation  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)