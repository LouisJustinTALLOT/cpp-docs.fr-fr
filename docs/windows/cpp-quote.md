---
title: cpp_quote | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38ecabcde55f49687abf7caff66fb2c316fab0fe
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871160"
---
# <a name="cppquote"></a>cpp_quote
Émet la chaîne spécifiée, sans guillemets, dans le fichier .idl généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Paramètres  
 *statement*  
 Une instruction C.  
  
## <a name="remarks"></a>Notes  
 Le **cpp_quote** attribut C++ est utile si vous souhaitez placer une directive de préprocesseur dans un fichier .idl.  
  
 Vous pouvez également utiliser **cpp_quote** et générer un fichier .h dans le cadre de la compilation MIDL. Par exemple, si vous avez un fichier d’en-tête C++ qui utilise des attributs IDL de C++, mais ne pouvez pas utiliser ce fichier pour une tâche, puis vous pouvez compiler pour créer un fichier .h de générés par MIDL, vous devez être en mesure d’utiliser.  
  
 Le **cpp_quote** attribut a les mêmes fonctionnalités que le [cpp_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [double](../windows/dual.md) pour obtenir un exemple, utilisez l’utilisation de **cpp_quote**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
