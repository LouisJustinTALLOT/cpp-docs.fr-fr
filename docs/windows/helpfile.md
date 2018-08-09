---
title: HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c2714c1418c5c9828322561ae1d7ca86dc6130a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647734"
---
# <a name="helpfile"></a>helpfile
Définit le nom du fichier d’aide pour une bibliothèque de types.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ helpfile(  
   "filename"  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *filename*  
 Le nom du fichier qui contient les rubriques d’aide.  
  
## <a name="remarks"></a>Notes  
 Le **helpfile** attribut C++ a les mêmes fonctionnalités que le [helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [module](../windows/module-cpp.md) pour obtenir un exemple montrant comment utiliser **helpfile**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, **propriété**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs d’interface](../windows/interface-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Attributs de méthode](../windows/method-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpContext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   