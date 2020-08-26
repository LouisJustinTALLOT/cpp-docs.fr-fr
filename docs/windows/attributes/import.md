---
title: Import (attribut COM C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: 6b146bdad7d870b534c371a4396993202cc83a4b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842310"
---
# <a name="import"></a>importer

Spécifie un autre fichier. idl,. ODL ou d’en-tête contenant les définitions que vous souhaitez référencer à partir de votre IDL principal.

## <a name="syntax"></a>Syntaxe

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Paramètres

*idl_file*<br/>
Nom d’un fichier. idl que vous souhaitez importer dans la bibliothèque de types du projet actif.

## <a name="remarks"></a>Notes

L’attribut **Import** C++ provoque l' `#import` placement d’une instruction sous l' `import "docobj.idl"` instruction dans le fichier. idl généré. L’attribut **Import** a les mêmes fonctionnalités que l’attribut MIDL [Import](/windows/win32/Midl/import) .

L’attribut d' **importation** place uniquement le fichier spécifié dans le fichier. idl qui sera généré par votre projet. l’attribut d' **importation** ne vous permet pas d’appeler des constructions dans le fichier spécifié à partir du code source de votre projet.  Pour appeler des constructions dans le fichier spécifié à partir du code source dans votre projet, utilisez [#import](../../preprocessor/hash-import-directive-cpp.md) et l' `embedded_idl` attribut ou vous pouvez inclure le fichier. h pour l' *idl_file*, si un fichier. h existe.

## <a name="example"></a>Exemple

Le code suivant :

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

produit le code suivant dans le fichier. idl généré :

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[inclusion](include-cpp.md)<br/>
[includelib (](includelib-cpp.md)
