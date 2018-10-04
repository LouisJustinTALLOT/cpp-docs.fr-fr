---
title: importidl (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d1c022a48ef5510f67355af3af1ff0a0e98ad4c4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790685"
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

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)  