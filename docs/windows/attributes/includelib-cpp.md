---
title: includelib (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 57f039eeae527dd03884b12e7d9eb424d87f597f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029998"
---
# <a name="includelib-c"></a>includelib (C++)

Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Paramètres

*name.idl*<br/>
Le nom du fichier .idl que vous souhaitez inclus dans le fichier .idl généré.

## <a name="remarks"></a>Notes

Le **includelib** attribut C++ génère un fichier .idl ou .h être inclus dans le fichier .idl généré, après la `importlib` instruction.

## <a name="example"></a>Exemple

Le code suivant est indiqué dans un fichier .cpp :

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Oui|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)