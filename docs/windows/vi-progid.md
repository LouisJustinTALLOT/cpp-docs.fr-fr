---
title: vi_progid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96843c9d977b15d7fe2c645c8f655cd59a42e401
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642046"
---
# <a name="viprogid"></a>vi_progid
Spécifie un formulaire indépendant de la version du ProgID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Paramètres  
 *name*  
 Le ProgID indépendants de la version qui représente l’objet.  
  
 ProgID présentent une version explicite de l’identificateur de classe (CLSID) utilisé pour identifier les objets COM/ActiveX.  
  
## <a name="remarks"></a>Notes  
 Le **vi_progid** attribut C++ vous permet de spécifier un ProgID indépendants de la version pour un objet COM. Un ProgID présente sous la forme *name1.name2.version*. Un ProgID indépendants de la version n’a pas un *version*. Il est possible de spécifier à la fois le `progid` et **vi_progid** attributs sur un `coclass`. Si vous ne spécifiez pas **vi_progid**, le ProgID indépendants de la version est la valeur spécifiée par le [progid](../windows/progid.md) attribut.  
  
 **vi_progid** implique la `coclass` d’attribut, autrement dit, si vous spécifiez **vi_progid**, il est la même chose que si vous définissiez le `coclass` et **vi_progid** attributs.  
  
 Le **vi_progid** attribut entraîne une classe soit automatiquement inscrite sous le nom spécifié. Le fichier .idl généré n’affichera pas la valeur ProgID.  
  
 Dans les projets ATL, si le [coclasse](../windows/coclass.md) attribut est également présent, le ProgID spécifié est utilisé par le `GetVersionIndependentProgID` (fonction) (insérées par les `coclass` attribut).  
  
## <a name="example"></a>Exemple  
 Consultez le [coclasse](../windows/coclass.md) exemple pour un exemple d’utilisation de **vi_progid**.  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Clé de progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   