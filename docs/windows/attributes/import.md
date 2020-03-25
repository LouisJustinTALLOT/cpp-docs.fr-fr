---
title: Import (C++ attribut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f2a0aa9a68c081e83a7a5278aa37a7fddac85416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166834"
---
# <a name="import"></a>importation

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

L’attribut **Import** C++ entraîne la placement d’une instruction `#import` sous l’instruction `import "docobj.idl"` dans le fichier. idl généré. L’attribut **Import** a les mêmes fonctionnalités que l’attribut MIDL [Import](/windows/win32/Midl/import) .

L’attribut d' **importation** place uniquement le fichier spécifié dans le fichier. idl qui sera généré par votre projet. l’attribut d' **importation** ne vous permet pas d’appeler des constructions dans le fichier spécifié à partir du code source de votre projet.  Pour appeler des constructions dans le fichier spécifié à partir du code source dans votre projet, utilisez [#import](../../preprocessor/hash-import-directive-cpp.md) et l’attribut `embedded_idl` ou vous pouvez inclure le fichier. h pour le *idl_file*, si un fichier. h existe.

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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
