---
title: coclasse | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bcae762c603f05ce11eae5d14eb2e182c666797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="coclass"></a>coclasse
Crée un objet COM, ce qui peut implémenter une interface COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[coclass]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **coclasse** attribut C++ place une construction de la coclasse dans le fichier .idl généré.  
  
 Lorsque vous définissez une coclasse, vous pouvez également spécifier le [uuid](../windows/uuid-cpp-attributes.md), [version](../windows/version-cpp.md), [threading](../windows/threading-cpp.md), [vi_progid](../windows/vi-progid.md), et [progid ](../windows/progid.md) attributs. Si l’un d’eux n’est pas spécifié, il sera généré.  
  
 Si les deux fichiers d’en-tête contiennent des classes avec le **coclasse** d’attribut et ne spécifiez pas un GUID, le compilateur utilise le même GUID pour les deux classes, et qui provoque une erreur MIDL.  Par conséquent, vous devez utiliser le `uuid` d’attribut lorsque vous utilisez **coclasse**.  
  
 **Projets ATL**  
  
 Lorsque cet attribut précède une définition de classe ou structure dans un projet ATL, elle :  
  
-   Injecte le code ou données pour prendre en charge d’inscription automatique pour l’objet.  
  
-   Injecte le code ou données pour prendre en charge une fabrique de classe COM pour l’objet.  
  
-   Injecte le code ou données pour implémenter **IUnknown** et rendre l’objet à un objet COM pouvant être créées.  
  
 Plus précisément, les classes de base suivantes sont ajoutées à l’objet cible :  
  
-   [Classe de CComCoClass](../atl/reference/ccomcoclass-class.md) fournit le modèle de fabrique et l’agrégation de la classe par défaut pour l’objet.  
  
-   [CComObjectRootEx classe](../atl/reference/ccomobjectrootex-class.md) a un modèle basé sur la classe de modèle de thread spécifiée par le [threading](../windows/threading-cpp.md) attribut. Si le **threading** attribut n’est pas spécifié, la valeur par défaut de modèle de thread est cloisonné.  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) est ajouté si le [noncreatable](../windows/noncreatable.md) attribut n’est pas spécifié pour l’objet cible.  
  
 Enfin, n’importe quel interface double n’est pas défini à l’aide d’un IDL incorporé est remplacé avec correspondant [IDispatchImpl](../atl/reference/idispatchimpl-class.md) classe. Si l’interface double est définie dans un IDL incorporé, l’interface particulier dans la liste de base n’est pas modifié.  
  
 Le **coclasse** attribut rend également les fonctions suivantes disponibles via le code injecté, ou dans le cas de `GetObjectCLSID`, comme une méthode statique dans la classe de base `CComCoClass`:  
  
-   `UpdateRegistry`enregistre les fabriques de classe de la classe cible.  
  
-   `GetObjectCLSID`, qui est liée à l’inscription, peut également servir à obtenir le CLSID de la classe cible.  
  
-   **GetObjectFriendlyName** par défaut retourne une chaîne au format «\<*nom de la classe cible*> `Object`». Si cette fonction est déjà présente, il n’est pas ajouté. Ajoutez cette fonction à la classe cible pour renvoyer un nom convivial que celui généré automatiquement.  
  
-   **GetProgID**, qui est liée à l’inscription, retourne la chaîne spécifiée par le [progid](../windows/progid.md) attribut.  
  
-   **GetVersionIndependentProgID** a les mêmes fonctionnalités que **GetProgID**, mais elle retourne la chaîne spécifiée avec [vi_progid](../windows/vi-progid.md).  
  
 Les modifications suivantes, qui sont liées au mappage COM, sont apportées à la classe cible :  
  
-   Un mappage COM est ajouté avec les entrées pour toutes les interfaces qui dérive de la classe cible et toutes les entrées spécifiées par le [Interface COM Points d’entrée](../mfc/com-interface-entry-points.md) attribut ou celles qui sont requises par le [agrégats](../windows/aggregates.md) attribut.  
  
-   Un [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto) macro est insérée dans le mappage COM.
  
 Le nom de la coclasse généré dans le fichier .idl pour la classe aura le même nom que la classe.  Par exemple, vous faites référence à l’exemple suivant, pour accéder à l’ID de classe pour une coclasse CMyClass, dans un client via le fichier d’en-tête généré par MIDL, utilisez CLSID_CMyClass.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **coclasse** attribut :  
  
```  
// cpp_attr_ref_coclass1.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface I {  
   HRESULT func();  
};  
  
[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),   
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]  
class CMyClass : public I {};  
```  
  
 L’exemple suivant montre comment substituer l’implémentation par défaut d’une fonction qui apparaît dans le code injecté par le **coclasse** attribut. Pour plus d’informations sur l’affichage de code injecté, consultez [/Fx](../build/reference/fx-merge-injected-code.md) . Les classes de base ou les interfaces que vous utilisez pour une classe s’affiche dans le code injecté.   En outre, si une classe est incluse par défaut dans le code injecté et que vous spécifiez explicitement cette classe comme base pour votre coclasse, le fournisseur de l’attribut utilise le formulaire spécifié dans votre code.  
  
```  
// cpp_attr_ref_coclass2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface bb {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class CMyClass : public bb {  
public:  
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs COM](../windows/com-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
 [TypeDef, Enum, Union et Struct (attributs)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)