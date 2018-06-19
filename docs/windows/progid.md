---
title: ProgID | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b2d2168b568c74c5404cc83bab1e5f77570773
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880431"
---
# <a name="progid"></a>progid
Spécifie le ProgID d’un objet COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Paramètres  
 *name*  
 Le ProgID qui représente l’objet.  
  
 ProgID présentent une version lisible de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.  
  
## <a name="remarks"></a>Notes  
 Le **progid** attribut C++ vous permet de spécifier le ProgID d’un objet COM. Un ProgID présente sous la forme *name1.name2.version*. Si vous ne spécifiez pas un *version* pour un ProgID, la version par défaut est 1. Si vous ne spécifiez pas *name1.name2*, le nom par défaut est *classname.classname*. Si vous ne spécifiez pas **progid** et que vous ne spécifiez pas **vi_progid**, *name1.name2* proviennent de **vi_progid** et (suivant séquentielles version de nombre) est ajoutée.  
  
 Si un bloc d’attributs qui utilise **progid** n’utilise pas également `uuid`, le compilateur doit rechercher le Registre afin de déterminer si un `uuid` existe pour le texte spécifié **progid**. Si **progid** n’est pas spécifié, la version (et le nom de la coclasse, si la création d’une coclasse) doit être utilisées pour générer un **progid**.  
  
 **ProgID** implique la **coclasse** d’attribut, autrement dit, si vous spécifiez **progid**, il s’agit de la même chose que la spécification de la **coclasse** et  **ProgID** attributs.  
  
 Le **progid** attribut entraîne une classe soit automatiquement inscrite sous le nom spécifié. Le fichier .idl généré n’affichera pas le **progid** valeur.  
  
 Lorsque cet attribut est utilisé dans un projet qui utilise ATL, le comportement de l’attribut change. En plus du comportement ci-dessus, les informations spécifiées avec cet attribut sont utilisées dans le **GetProgID** fonction, injectée par le **coclasse** attribut. Pour plus d’informations, consultez la [coclasse](../windows/coclass.md) attribut.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [coclasse](../windows/coclass.md) pour un exemple d’utilisation de **progid**.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Clé progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
