---
title: importidl (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 8f3c2c5c67ac216d096d1082814c561698f3f732
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842245"
---
# <a name="importidl"></a>importidl

Insère le fichier. idl spécifié dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Paramètres

*idl_file*<br/>
Identifie le nom du fichier. idl que vous souhaitez fusionner avec le fichier. idl qui sera généré pour votre application.

## <a name="remarks"></a>Notes

L’attribut C++ **importidl** place la section en dehors du bloc de bibliothèque (dans *idl_file*) dans le fichier. idl généré par votre programme et la section de la bibliothèque (dans *idl_file*) dans la section Bibliothèque du fichier. idl généré de votre programme.

Vous souhaiterez peut-être utiliser **importidl**, par exemple, si vous souhaitez utiliser un fichier. idl codé manuellement avec votre fichier. idl généré.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[inclusion](include-cpp.md)<br/>
[includelib (](includelib-cpp.md)
