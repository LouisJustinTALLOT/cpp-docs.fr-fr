---
title: version (C++) | Microsoft Docs
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
ms.openlocfilehash: 2c2d0c72ffbb805b526429562a5f39a09285b70f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642277"
---
# <a name="version-c"></a>version (C++)
Identifie une version particulière entre plusieurs versions d’une classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ version(  
   "version"  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *version*  
 Le numéro de version de la `coclass`. Si non spécifié, 1.0 sera placé dans le fichier .idl.  
  
## <a name="remarks"></a>Notes  
 Le **version** attribut C++ a les mêmes fonctionnalités que le [version](http://msdn.microsoft.com/library/windows/desktop/aa367306) attribut MIDL et est transféré vers le fichier .idl généré.  
  
## <a name="example"></a>Exemple  
 Consultez le [peut être liée](../windows/bindable.md) exemple pour un exemple d’utilisation de **version**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|**coclass**|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de compilateur](../windows/compiler-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   