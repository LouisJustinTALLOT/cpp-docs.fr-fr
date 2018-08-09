---
title: Threading (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0e8b13a74c5b232e2662f80fc1cc8f80a1ffc9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652999"
---
# <a name="threading-c"></a>thread (C++)
Spécifie le modèle de thread pour un objet COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ threading(  
   model=enumeration  
) ]  
```  
  
### <a name="parameters"></a>Paramètres  
 *modèle* (facultatif)  
 L’un des modèles de threads suivants :  
  
-   `apartment` (modèle de thread cloisonné)  
  
-   `neutral` (Composants de .NET framework sans interface utilisateur)  
  
-   `single` (thread simple)  
  
-   `free` (threading libre)  
  
-   `both` (cloisonnement et modèle de thread libre)  
  
 La valeur par défaut est `apartment`.  
  
## <a name="remarks"></a>Notes  
 Le **threading** attribut C++ n’apparaît pas dans le fichier .idl généré, mais sera utilisé dans l’implémentation de votre objet COM.  
  
 Dans les projets ATL, si le [coclasse](../windows/coclass.md) attribut est également présent, le modèle de thread spécifié par *modèle* est passé comme paramètre de modèle pour le [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) classe , inséré par la `coclass` attribut.  
  
 Le **threading** attribut protège également l’accès à un [event_source](../windows/event-source.md).  
  
## <a name="example"></a>Exemple  
 Consultez le [concédé sous licence](../windows/licensed.md) exemple pour un exemple d’utilisation de **threading**.  
  
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
 [Attributs COM](../windows/com-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [Prise en charge le multithreading pour le Code plus ancien (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Cloisonnements neutres](http://msdn.microsoft.com/library/windows/desktop/ms681813)   