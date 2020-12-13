---
description: 'En savoir plus sur : importidl'
title: importidl (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: b10caa9f4b1467727c70b6d968ca6aa33b58da0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329877"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[inclusion](include-cpp.md)<br/>
[includelib (](includelib-cpp.md)
