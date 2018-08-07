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
ms.openlocfilehash: 933fc1db2a890fedd9d725c49bbeb6c363e2f4c8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569636"
---
# <a name="entry"></a>entry
Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
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