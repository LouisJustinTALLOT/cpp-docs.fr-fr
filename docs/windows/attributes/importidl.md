---
title: importidl (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166820"
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

L’attribut **importidl** C++ place la section en dehors du bloc de bibliothèque (dans *idl_file*) dans le fichier. idl généré par votre programme et la section de la bibliothèque (dans *idl_file*) dans la section Bibliothèque du fichier. idl généré de votre programme.

Vous souhaiterez peut-être utiliser **importidl**, par exemple, si vous souhaitez utiliser un fichier. idl codé manuellement avec votre fichier. idl généré.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
