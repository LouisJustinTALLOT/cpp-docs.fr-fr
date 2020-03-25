---
title: includelib ((C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214841"
---
# <a name="includelib-c"></a>includelib (C++)

Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Paramètres

*nom. idl*<br/>
Nom du fichier. idl que vous souhaitez inclure dans le fichier. idl généré.

## <a name="remarks"></a>Notes

L’attribut **includelib (** C++ entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré, après l’instruction `importlib`.

## <a name="example"></a>Exemple

Le code suivant est affiché dans un fichier. cpp :

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Oui|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
