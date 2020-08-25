---
title: includelib ((attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 30e84a6c82ec25e07ca0eb08f64c7aa5b560e9e7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830694"
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

L’attribut C++ **includelib (** entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré, après l' `importlib` instruction.

## <a name="example"></a>Exemple

Le code suivant est affiché dans un fichier. cpp :

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Repeatable Read**|Oui|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[inclusion](include-cpp.md)<br/>
[importlib](importlib.md)
