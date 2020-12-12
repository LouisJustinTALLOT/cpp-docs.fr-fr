---
description: 'En savoir plus sur : importlib'
title: importlib (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: f3000be3415ed944d621ebcd36442e33951efc84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114947"
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

L’attribut C++ **importlib** provoque le `importlib` placement d’une instruction dans le bloc de bibliothèque du fichier. idl généré. L’attribut **importlib** a les mêmes fonctionnalités que l’attribut MIDL [importlib](/windows/win32/Midl/importlib) .

## <a name="example"></a>Exemple

Le code suivant montre un exemple d’utilisation de **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
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
[importidl](importidl.md)<br/>
[inclusion](include-cpp.md)<br/>
[includelib (](includelib-cpp.md)
