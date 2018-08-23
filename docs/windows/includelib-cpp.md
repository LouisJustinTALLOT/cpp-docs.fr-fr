---
title: includelib (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 551ae176504e3bbbca034ca91894ef793ea268fd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584340"
---
# <a name="includelib-c"></a>includelib (C++)

Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ includelib(
   name.idl
) ];
```

### <a name="parameters"></a>Paramètres

*Name.idl*  
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

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs autonomes](../windows/stand-alone-attributes.md)  
[import](../windows/import.md)  
[importidl](../windows/importidl.md)  
[include](../windows/include-cpp.md)  
[importlib](../windows/importlib.md)  