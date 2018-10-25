---
title: Importer (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 046a6eb0d1033efb44dd9f34806e747e1fafd700
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071113"
---
# <a name="import"></a>d'importation

Spécifie un autre fichier .idl, .odl ou en-tête contenant les définitions que vous souhaitez référencer à partir de votre principal IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Paramètres

*idl_file*<br/>
Le nom d’un fichier .idl que vous souhaitez importer dans la bibliothèque de types du projet actuel.

## <a name="remarks"></a>Notes

Le **importer** C++ attribut entraîne une `#import` instruction à être placé sous le `import "docobj.idl"` instruction dans le fichier .idl généré. Le **importer** attribut a les mêmes fonctionnalités que le [importer](/windows/desktop/Midl/import) attribut MIDL.

Le **importer** attribut place uniquement le fichier spécifié dans le fichier .idl qui doit être généré par votre projet ; le **importer** attribut ne permet pas d’appeler des constructions dans le fichier spécifié à partir de code source dans votre projet.  Pour appeler les constructions dans le fichier spécifié à partir du code source dans votre projet, soit utiliser [#import](../../preprocessor/hash-import-directive-cpp.md) et `embedded_idl` attribut, ou vous pouvez inclure le fichier .h pour la *idl_file*, s’il existe un fichier .h.

## <a name="example"></a>Exemple

L'exemple de code suivant :

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

génère le code suivant dans le fichier .idl généré :

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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)