---
title: DontUseNewUseMake::operator new, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b849c7578b29a3d4595a9ecd07c4339dc751e9dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652947"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *__unnamed0*  
 Un paramètre sans nom qui spécifie le nombre d’octets de mémoire à allouer.  
  
 *sélection élective*  
 Le type doit être allouée.  
  
## <a name="return-value"></a>Valeur de retour  
 Fournit un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur **nouveau**.  
  
## <a name="remarks"></a>Notes  
 Surcharge d’opérateur **nouveau** et empêche l’utilisation dans `RuntimeClass`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [DontUseNewUseMake (classe)](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)