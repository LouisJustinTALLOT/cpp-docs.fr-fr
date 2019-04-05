---
title: importidl (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 9db62d4f2a36b8cc0592c924b113077a758915c0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029912"
---
# <a name="importidl"></a>importidl

Insère le fichier .idl spécifié dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Paramètres

*idl_file*<br/>
Identifie le nom du fichier .idl que vous souhaitez fusionner avec le fichier .idl qui doit être généré pour votre application.

## <a name="remarks"></a>Notes

Le **importidl** attribut C++ place la section en dehors du bloc de bibliothèque (dans *idl_file*) dans le fichier .idl généré de votre programme et de la section de la bibliothèque (dans *idl_file*) dans la bibliothèque de section de votre programme généré le fichier .idl.

Vous pouvez souhaiter utiliser **importidl**, par exemple, si vous souhaitez utiliser un fichier .idl codé manuellement avec votre fichier .idl généré.

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[d'importation](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)