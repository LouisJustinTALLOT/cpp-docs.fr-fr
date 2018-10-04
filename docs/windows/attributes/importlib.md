---
title: importlib (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd43dd8a0fb4660cbe0c631bcb3477ef3d26f0f6
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790985"
---
# <a name="importlib"></a>importlib

Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.

## <a name="syntax"></a>Syntaxe

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>Paramètres

*tlb_file*<br/>
Nom d'un fichier .tlb, entre guillemets, que vous souhaitez importer dans la bibliothèque de types du projet actuel.

## <a name="remarks"></a>Notes

Le **importlib** C++ attribut entraîne une `importlib` instruction à placer dans le bloc de bibliothèque du fichier .idl généré. Le **importlib** attribut a les mêmes fonctionnalités que le [importlib](/windows/desktop/Midl/importlib) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant montre un exemple montrant comment utiliser **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)