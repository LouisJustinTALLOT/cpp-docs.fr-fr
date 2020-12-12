---
description: 'En savoir plus sur : includelib ((C++)'
title: includelib ((attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 9a7565a931a865b69f0da95da9e92481b27de3b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321348"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Oui|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[inclusion](include-cpp.md)<br/>
[importlib](importlib.md)
