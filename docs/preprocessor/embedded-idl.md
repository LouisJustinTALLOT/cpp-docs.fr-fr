---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: c46924d2757d01a934c21a70f23e6556f6a10fd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389344"
---
# <a name="embeddedidl"></a>embedded_idl

**Spécifique à C++**

Indique que la bibliothèque de types est écrite dans le fichier .tlh et que le code généré par attributs est conservé.

## <a name="syntax"></a>Syntaxe

```
embedded_idl[("param")]
```

### <a name="parameters"></a>Paramètres

*param*<br/>
Peut avoir l'une des deux valeurs suivantes :

- **emitidl**: Les informations de type importées à partir de la typelib sera présentes dans le fichier IDL généré pour le projet avec attributs.  Il s'agit de la valeur par défaut qui sera appliquée si vous ne spécifiez pas de paramètre pour `embedded_idl`.

- **no_emitidl**: Informations de type importées à partir du typelib ne seront pas présentes dans le fichier IDL généré pour le projet avec attributs.

## <a name="example"></a>Exemple

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>Notes

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)