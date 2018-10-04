---
title: module (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71ada4927d1a29c2f4d9a95ed93554b0cbffc92d
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790736"
---
# <a name="module-c"></a>module (C++)

Définit le bloc de bibliothèque dans le fichier .idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Paramètres

*type*<br/>
(Facultatif) Peut prendre l’une des opérations suivantes :

- `dll` Ajoute des fonctions et des classes qui permettent à la DLL résultante de fonctionner comme serveur COM in-process. Valeur par défaut.

- `exe` Ajoute des fonctions et des classes qui permettent la résultant exécutable de fonctionner comme un serveur hors processus COM.

- `service` Ajoute des fonctions et des classes qui permettent la résultant exécutable de fonctionner comme un service NT.

- `unspecified` Désactive l’injection de code ATL associé à l’attribut de module : injection de la classe ATL Module, instance globale _AtlModule et entrée des fonctions de point. Ne désactive pas l’injection de code ATL due à d’autres attributs dans le projet.

*name*<br/>
(Facultatif) Le nom du bloc de bibliothèque.

*version*<br/>
(Facultatif) Le numéro de version que vous souhaitez affecter au bloc de bibliothèque. La valeur par défaut est 1,0.

*uuid*<br/>
ID unique de la bibliothèque. Si vous omettez ce paramètre, un ID est généré automatiquement pour la bibliothèque. Vous devrez peut-être récupérer le *uuid* de votre bloc de bibliothèque, vous pouvez ainsi faire en utilisant l’identificateur **__uuidof (** *nom_bibliothèque* **)**.

*lcid*<br/>
Paramètre de localisation. Consultez [lcid](/windows/desktop/Midl/lcid) pour plus d’informations.

*control*<br/>
(Facultatif) Spécifie que toutes les coclasses dans la bibliothèque sont des contrôles.

*helpstring*<br/>
Spécifie la bibliothèque de types.

*helpstringdll*<br/>
(Facultatif) Définit le nom du fichier .dll à utiliser pour effectuer une recherche de chaîne du document. Consultez [helpstringdll](/windows/desktop/Midl/helpstringdll) pour plus d’informations.

*helpfile*<br/>
(Facultatif) Le nom de la **aide** fichier pour la bibliothèque de types.

*helpcontext*<br/>
(Facultatif) Le **ID d’aide** pour cette bibliothèque de types.

*helpstringcontext*<br/>
(Facultatif) Consultez [helpstringcontext](helpstringcontext.md) pour plus d’informations.

*hidden*<br/>
(Facultatif) Empêche l’affichage de la totalité de la bibliothèque. Cette utilisation est destinée aux contrôles. Les hôtes doivent créer une bibliothèque de types qui encapsule le contrôle avec des propriétés étendues. Consultez le [masqué](/windows/desktop/Midl/hidden) attribut MIDL pour plus d’informations.

*restricted*<br/>
(Facultatif) Membres de la bibliothèque ne peut pas être appelées arbitrairement. Consultez le [restreint](/windows/desktop/Midl/restricted) attribut MIDL pour plus d’informations.

*custom*<br/>
(Facultatif) Un ou plusieurs attributs ; Ceci est similaire à la [personnalisé](custom-cpp.md) attribut. Le premier paramètre de *personnalisé* est le GUID de l’attribut. Exemple :

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
ID de ressource de chaîne du fichier .rgs utilisé pour enregistrer l’ID d’application de la DLL, de l’exécutable ou du service. Quand le module est de type service, cet argument sert également à obtenir l’ID de la chaîne contenant le nom du service.

> [!NOTE]
> Le fichier .rgs et la chaîne contenant le nom du service doivent tous deux contenir la même valeur numérique.

## <a name="remarks"></a>Notes

Sauf si vous spécifiez le *restreint* paramètre [emitidl](emitidl.md), **module** est obligatoire dans tout programme qui utilise des attributs C++.

Un bloc de bibliothèque est créé si, outre le **module** attribut, le code source utilise également [dispinterface](dispinterface.md), [double](dual.md), [objet](object-cpp.md), ou un attribut qui implique [coclasse](coclass.md).

Un seul bloc de bibliothèque est autorisé dans un fichier .idl. Les entrées de module multiples dans le code source sont fusionnées, les valeurs de paramètres les plus récentes étant implémentées.

Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement décrit ci-dessus, l’attribut insère également un objet global (appelé `_AtlModule`) du type correct et du code de prise en charge supplémentaire. Si l’attribut est autonome, il insère une classe dérivée du type de module approprié. Si l’attribut est appliqué à une classe, il ajoute une classe de base du type de module approprié. Le type correct est déterminé par la valeur de la *type* paramètre :

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) est utilisée comme classe de base et l’entrée DLL standard requis pour un serveur COM de points. Ces points d’entrée sont [DllMain](/windows/desktop/Dlls/dllmain), [DllRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), et [ DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) est utilisée comme classe de base et le point d’entrée d’exécutable standard [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) est utilisée comme classe de base et le point d’entrée d’exécutable standard [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **unspecified**

   Désactive l’injection de code ATL associé à l’attribut de module.

## <a name="example"></a>Exemple

Le code suivant montre comment créer un bloc de bibliothèque dans le fichier .idl généré.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Le code suivant montre que vous pouvez fournir votre propre implémentation d’une fonction qui s’affiche dans le code injecté suite à l’utilisation de **module**. Consultez [/Fx](../../build/reference/fx-merge-injected-code.md) pour plus d’informations sur l’affichage de code injecté. Pour substituer l’une des fonctions insérées par l’attribut **module** , créez une classe qui contiendra votre implémentation de la fonction et faites en sorte que l’attribut **module** s’applique à cette classe.

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Bibliothèque](/windows/desktop/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)  