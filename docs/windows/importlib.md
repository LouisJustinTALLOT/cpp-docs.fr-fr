---
title: importlib | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21b97e50fa03861245a0c0881963387dd8a3102
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876756"
---
# <a name="importlib"></a>importlib
Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### <a name="parameters"></a>Paramètres  
 *tlb_file*  
 Nom d'un fichier .tlb, entre guillemets, que vous souhaitez importer dans la bibliothèque de types du projet actuel.  
  
## <a name="remarks"></a>Notes  
 Le **importlib** C++ attribut entraîne une `importlib` instruction doit être placé dans le bloc de bibliothèque du fichier .idl généré. Le **importlib** attribut a les mêmes fonctionnalités que le [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre un exemple montrant comment utiliser **importlib**:  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du compilateur](../windows/compiler-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [Importation](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [Inclure](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)