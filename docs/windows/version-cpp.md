---
title: version (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43da63d75d3541915eba3e561ee08fe1048fa579
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890607"
---
# <a name="version-c"></a>version (C++)
Identifie une version particulière entre plusieurs versions d’une classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *version*  
 Le numéro de version de la coclasse. Si non spécifié, 1.0 sera placé dans le fichier .idl.  
  
## <a name="remarks"></a>Notes  
 Le **version** attribut C++ a les mêmes fonctionnalités que le [version](http://msdn.microsoft.com/library/windows/desktop/aa367306) attribut MIDL et est passée au fichier .idl généré.  
  
## <a name="example"></a>Exemple  
 Consultez le [pouvant être liés](../windows/bindable.md) exemple pour un exemple d’utilisation de **version**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclass**|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du compilateur](../windows/compiler-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
