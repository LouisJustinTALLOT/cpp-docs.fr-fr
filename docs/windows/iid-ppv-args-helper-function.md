---
title: IID_PPV_ARGS_Helper (fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882340"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper (fonction)
Vérifie que le type de l’argument spécifié dérive le `IUnknown` interface.  
  
> [!IMPORTANT]
>  Cette spécialisation de modèle prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code. Utilisez [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type d’argument `pp`.  
  
 `pp`  
 Pointeur doublement indirect.  
  
## <a name="return-value"></a>Valeur de retour  
 Argument `pp` castée en pointeur-à-un en pointeur vers `void`.  
  
## <a name="remarks"></a>Notes  
 Une erreur de compilation est générée si le paramètre de modèle `T` ne dérive pas de `IUnknown`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (bibliothèque Windows Runtime)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)