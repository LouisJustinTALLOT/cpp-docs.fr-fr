---
title: coclasse (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 76540e90fef2e840b91bb07f570a7b8c0987eb10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168329"
---
# <a name="coclass"></a>coclasse

Crée un objet COM, qui peut implémenter une interface COM.

## <a name="syntax"></a>Syntaxe

```cpp
[coclass]
```

## <a name="remarks"></a>Notes

L’attribut **coclass** C++ place une construction coclasse dans le fichier. idl généré.

Lors de la définition d’une coclasse, vous pouvez également spécifier les attributs [UUID](uuid-cpp-attributes.md), [version](version-cpp.md), [Threading](threading-cpp.md), [vi_progid](vi-progid.md)et [ProgID](progid.md) . Si l’un d’eux n’est pas spécifié, il sera généré.

Si deux fichiers d’en-tête contiennent des classes avec l’attribut **coclass** et ne spécifient pas de GUID, le compilateur utilisera le même GUID pour les deux classes et cela entraînera une erreur MIDL.  Par conséquent, vous devez utiliser l’attribut `uuid` lorsque vous utilisez **coclass**.

**Projets ATL**

Quand cet attribut précède une définition de classe ou de structure dans un projet ATL, il :

- Injecte du code ou des données pour prendre en charge l’inscription automatique de l’objet.

- Injecte du code ou des données pour prendre en charge une fabrique de classe COM pour l’objet.

- Injecte du code ou des données pour implémenter `IUnknown` et faire de l’objet un objet pouvant être créé par COM.

Plus précisément, les classes de base suivantes sont ajoutées à l’objet cible :

- La [classe CComCoClass](../../atl/reference/ccomcoclass-class.md) fournit la fabrique de classe et le modèle d’agrégation par défaut pour l’objet.

- La [classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) a un modèle basé sur la classe de modèle de thread spécifiée par l’attribut de [thread](threading-cpp.md) . Si l’attribut `threading` n’est pas spécifié, le modèle de thread par défaut est Apartment.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) est ajouté si l’attribut [noncreatable](noncreatable.md) n’est pas spécifié pour l’objet cible.

Enfin, toute interface double qui n’est pas définie à l’aide d’un IDL incorporé est remplacée par la classe [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) correspondante. Si l’interface double est définie dans un IDL incorporé, l’interface particulière de la liste de base n’est pas modifiée.

L’attribut **coclass** rend également les fonctions suivantes disponibles par le biais du code injecté, ou dans le cas de `GetObjectCLSID`, comme une méthode statique dans la classe de base `CComCoClass`:

- `UpdateRegistry` inscrit les fabriques de classes de la classe cible.

- `GetObjectCLSID`, qui est lié à l’inscription, peut également être utilisé pour obtenir le CLSID de la classe cible.

- `GetObjectFriendlyName` par défaut retourne une chaîne au format «\<nom de la *classe cible*> `Object`». Si cette fonction est déjà présente, elle n’est pas ajoutée. Ajoutez cette fonction à la classe cible pour retourner un nom plus convivial que celui généré automatiquement.

- `GetProgID`, qui est lié à l’inscription, retourne la chaîne spécifiée avec l’attribut [ProgID](progid.md) .

- `GetVersionIndependentProgID` a les mêmes fonctionnalités que `GetProgID`, mais retourne la chaîne spécifiée avec [vi_progid](vi-progid.md).

Les modifications suivantes, qui sont liées au mappage COM, sont apportées à la classe cible :

- Un mappage COM est ajouté avec des entrées pour toutes les interfaces dérivees de la classe cible et toutes les entrées spécifiées par l’attribut des points d’entrée de l' [interface com](../../mfc/com-interface-entry-points.md) ou celles requises par l’attribut [Aggregates](aggregates.md) .

- Une macro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) est insérée dans la table com.

Le nom de la coclasse générée dans le fichier. idl de la classe porte le même nom que la classe.  Par exemple, et en faisant référence à l’exemple suivant, pour accéder à l’ID de classe d’une coclasse `CMyClass`, dans un client par le biais du fichier d’en-tête généré par MIDL, utilisez `CLSID_CMyClass`.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l’attribut **coclass** :

```cpp
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

L’exemple suivant montre comment substituer l’implémentation par défaut d’une fonction qui s’affiche dans le code injecté par l’attribut **coclass** . Pour plus d’informations sur l’affichage de code injecté, consultez [/Fx](../../build/reference/fx-merge-injected-code.md) . Toutes les classes ou interfaces de base que vous utilisez pour une classe s’affichent dans le code injecté. De plus, si une classe est incluse par défaut dans le code injecté et que vous spécifiez explicitement cette classe comme base pour votre coclasse, le fournisseur d’attributs utilisera le formulaire spécifié dans votre code.

```cpp
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
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs COM](com-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
