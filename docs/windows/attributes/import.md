---
description: 'En savoir plus sur : importer'
title: Import (attribut COM C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: a3ebb7aa625c0a422197662973985275647a049f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321400"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[inclusion](include-cpp.md)<br/>
[includelib (](includelib-cpp.md)
