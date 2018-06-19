---
title: Activationfactory::Release, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2617df132f31d63379a3bd27a49409b1599a090
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854835"
---
# <a name="activationfactoryrelease-method"></a>ActivationFactory::Release, méthode
Décrémente le décompte de références de l’objet ActivationFactory actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ActivationFactory, classe](../windows/activationfactory-class.md)