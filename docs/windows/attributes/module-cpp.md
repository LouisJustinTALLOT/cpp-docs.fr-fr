---
description: 'En savoir plus sur : module (C++)'
title: module (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 1780ebcb89e7d19f3f3a4c2656d383725d85657a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327481"
---
# <a name="module-c"></a>module (C++)

Définit le bloc de bibliothèque dans le fichier .idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Facultatif Il peut s’agir de l’un des éléments suivants :

- `dll` Ajoute des fonctions et des classes qui permettent à la DLL résultante de fonctionner en tant que serveur COM in-process. Il s’agit de la valeur par défaut.

- `exe` Ajoute des fonctions et des classes qui permettent à l’exécutable résultant de fonctionner comme un serveur COM hors processus.

- `service` Ajoute des fonctions et des classes qui permettent à l’exécutable résultant de fonctionner en tant que service NT.

- `unspecified` Désactive l’injection de code ATL associé à l’attribut de module : l’injection de classe de module ATL, les _AtlModule d’instances globales et les fonctions de point d’entrée. Ne désactive pas l’injection de code ATL due à d’autres attributs dans le projet.

*name*<br/>
Facultatif Nom du bloc de bibliothèque.

*version*<br/>
Facultatif Numéro de version que vous souhaitez affecter au bloc de bibliothèque. La valeur par défaut est 1,0.

*uuid*<br/>
ID unique de la bibliothèque. Si vous omettez ce paramètre, un ID est généré automatiquement pour la bibliothèque. Vous devrez peut-être récupérer l’ *uuid* de votre bloc de bibliothèque, ce que vous pouvez faire à l’aide de l’identificateur **__uuidof(** *nom_bibliothèque* **)**.

*lcid*<br/>
Paramètre de localisation. Pour plus d’informations, consultez [lcid](/windows/win32/Midl/lcid) .

*control*<br/>
Facultatif Spécifie que toutes les coclasses dans la bibliothèque sont des contrôles.

*helpstring*<br/>
Spécifie la bibliothèque de types.

*helpstringdll*<br/>
Facultatif Définit le nom du fichier. dll à utiliser pour effectuer une recherche de chaîne de document. Pour plus d’informations, consultez [helpstringdll](/windows/win32/Midl/helpstringdll) .

*helpfile*<br/>
Facultatif Nom du fichier d' **aide** pour la bibliothèque de types.

*helpcontext*<br/>
Facultatif **ID d’aide** pour cette bibliothèque de types.

*helpstringcontext*<br/>
Facultatif Pour plus d’informations, consultez [helpstringcontext](helpstringcontext.md) .

*masquer*<br/>
Facultatif Empêche l’affichage de la bibliothèque entière. Cette utilisation est destinée aux contrôles. Les hôtes doivent créer une bibliothèque de types qui encapsule le contrôle avec des propriétés étendues. Pour plus d’informations, consultez l’attribut MIDL [hidden](/windows/win32/Midl/hidden) .

*sensible*<br/>
Facultatif Les membres de la bibliothèque ne peuvent pas être appelés de façon arbitraire. Pour plus d’informations, consultez l’attribut MIDL [restricted](/windows/win32/Midl/restricted) .

*propre*<br/>
Facultatif Un ou plusieurs attributs ; Cela est similaire à l’attribut [personnalisé](custom-cpp.md) . Le premier paramètre de *Custom* est le GUID de l’attribut. Par exemple :

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
ID de ressource de chaîne du fichier .rgs utilisé pour enregistrer l’ID d’application de la DLL, de l’exécutable ou du service. Quand le module est de type service, cet argument sert également à obtenir l’ID de la chaîne contenant le nom du service.

> [!NOTE]
> Le fichier .rgs et la chaîne contenant le nom du service doivent tous deux contenir la même valeur numérique.

## <a name="remarks"></a>Notes

*module* est obligatoire dans tout programme qui utilise des attributs C++, sauf si vous spécifiez le paramètre [restricted](emitidl.md)pour **emitidl** .

Un bloc de bibliothèque est créé si, en plus de l’attribut **module** , le code source utilise également [dispinterface](dispinterface.md), [double](dual.md), [object](object-cpp.md)ou un attribut qui implique [coclass](coclass.md).

Un seul bloc de bibliothèque est autorisé dans un fichier .idl. Les entrées de module multiples dans le code source sont fusionnées, les valeurs de paramètres les plus récentes étant implémentées.

Si vous utilisez cet attribut dans un projet qui utilise ATL, le comportement de l’attribut change. Outre le comportement ci-dessus, l’attribut insère également un objet global (appelé `_AtlModule` ) du type correct et du code de prise en charge supplémentaire. Si l’attribut est autonome, il insère une classe dérivée du type de module approprié. Si l’attribut est appliqué à une classe, il ajoute une classe de base du type de module approprié. Le type correct est déterminé par la valeur du paramètre de *type* :

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) est utilisé comme classe de base et comme points d’entrée de DLL standard requis pour un serveur COM. Ces points d’entrée sont [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)et [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- `type` = **exécutable**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) est utilisé comme classe de base et comme point d’entrée d’exécutable standard [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **services**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) est utilisé comme classe de base et comme point d’entrée d’exécutable standard [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **non spécifié**

   Désactive l’injection de code ATL associé à l’attribut de module.

## <a name="example"></a>Exemple

Le code suivant montre comment créer un bloc de bibliothèque dans le fichier .idl généré.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Le code suivant montre que vous pouvez fournir votre propre implémentation d’une fonction qui s’affiche dans le code injecté suite à l’utilisation de **module**. Pour plus d’informations sur l’affichage de code injecté, consultez [/Fx](../../build/reference/fx-merge-injected-code.md) . Pour substituer l’une des fonctions insérées par l’attribut **module** , créez une classe qui contiendra votre implémentation de la fonction et faites en sorte que l’attribut **module** s’applique à cette classe.

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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Bibliothèque](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)
