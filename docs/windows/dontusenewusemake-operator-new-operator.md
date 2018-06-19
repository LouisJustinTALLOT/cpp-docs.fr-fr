---
title: DontUseNewUseMake::operator new, opérateur | Documents Microsoft
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
ms.openlocfilehash: 9785ea27c79ff0a118ff3697a22804c520b265ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873678"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `__unnamed0`  
 Un paramètre sans nom qui spécifie le nombre d’octets de mémoire à allouer.  
  
 `placement`  
 Le type à allouer.  
  
## <a name="return-value"></a>Valeur de retour  
 Offre un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur `new`.  
  
## <a name="remarks"></a>Notes  
 Surcharge d’opérateur `new` et empêche l’utilisation de RuntimeClass.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [DontUseNewUseMake (classe)](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)