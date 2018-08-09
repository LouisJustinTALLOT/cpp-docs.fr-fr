---
title: ActivationFactoryCallback (fonction) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 858232702367aef62d0228f2e8653774896bd87f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647181"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (fonction)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *activationId*  
 Handle vers une chaîne qui spécifie un nom de classe runtime.  
  
 *ppFactory*  
 Lorsque cette opération se termine, une fabrique d’activation qui correspond au paramètre *activationId*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. HRESULT d’échec probable sont CLASS_E_CLASSNOTAVAILABLE et E_INVALIDARG.  
  
## <a name="remarks"></a>Notes  
 Obtient la fabrique d’activation pour l’ID d’activation spécifié.  
  
 Le Runtime Windows appelle cette fonction de rappel pour demander un objet spécifié par son nom de classe runtime.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)