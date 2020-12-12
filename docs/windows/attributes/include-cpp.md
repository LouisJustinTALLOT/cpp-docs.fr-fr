---
description: 'En savoir plus sur : include (C++)'
title: include (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: c6d12b9d8826ce84de0c01aaf055f5a4176fea10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321361"
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

L’attribut **include** C++ provoque l’insertion d’une `#include` instruction sous l' `import "docobj.idl"` instruction dans le fichier. idl généré.

L’attribut **include** C++ a les mêmes fonctionnalités que l’attribut MIDL [include](/windows/win32/Midl/include) .

## <a name="example"></a>Exemple

Le code suivant montre un exemple d’utilisation de la méthode **include**. Pour cet exemple, le fichier include. h contient uniquement une `#include` instruction.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
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
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib (](includelib-cpp.md)<br/>
[importlib](importlib.md)
