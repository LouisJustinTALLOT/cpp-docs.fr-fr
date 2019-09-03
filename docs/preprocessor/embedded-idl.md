---
title: attribut d’importation embedded_idl
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216330"
---
# <a name="embedded_idl-import-attribute"></a>attribut d’importation embedded_idl

**C++Plus**

Spécifie si la bibliothèque de types est écrite `.tlh` dans le fichier avec le code généré par attribut conservé.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>Paramètres

**emitidl**\
Les informations de type importées à partir de la *bibliothèque de types* sont présentes dans le IDL généré pour le projet avec attributs. Ce comportement est le comportement par défaut et est appliqué si vous ne spécifiez pas de `embedded_idl`paramètre pour.

**"no_emitidl"** \
Les informations de type importées à partir de la *bibliothèque de types* ne sont pas présentes dans le IDL généré pour le projet avec attributs.

## <a name="example"></a>Exemple

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
