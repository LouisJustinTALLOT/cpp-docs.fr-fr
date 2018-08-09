---
title: entrée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f644df2969954187aa4506d2cc1d04d140f88de3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642885"
---
# <a name="entry"></a>entry
Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ entry(  
   id  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 L’ID du point d’entrée.  
  
## <a name="remarks"></a>Notes  
 Le **entrée** attribut C++ a les mêmes fonctionnalités que le [entrée](http://msdn.microsoft.com/library/windows/desktop/aa366815) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [idl_module](../windows/idl-module.md) pour un exemple d’utilisation de **entrée**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Attribut `idl_module`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   