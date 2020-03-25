---
title: includeC++ (attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 39f991bb036dce1c50a9d2ee800d3fec65af7c55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166781"
---
# <a name="include-c"></a>include (C++)

Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Paramètres

*header_file*<br/>
Nom d’un fichier que vous souhaitez inclure dans le fichier. idl généré.

## <a name="remarks"></a>Notes

Avec l’attribut **include** C++ , une instruction `#include` est placée sous l’instruction `import "docobj.idl"` dans le fichier. idl généré.

L’attribut **include** C++ a les mêmes fonctionnalités que l’attribut MIDL [include](/windows/win32/Midl/include) .

## <a name="example"></a>Exemple

Le code suivant montre un exemple d’utilisation de la méthode **include**. Pour cet exemple, le fichier include. h contient uniquement une instruction `#include`.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
