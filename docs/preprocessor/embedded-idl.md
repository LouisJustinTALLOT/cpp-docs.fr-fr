---
description: 'En savoir plus sur les éléments suivants : embedded_idl l’attribut import'
title: embedded_idl l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: a56c6e664c082db4b6eac078b7133a1ead947d3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300591"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl l’attribut d’importation

**Section spécifique à C++**

Spécifie si la bibliothèque de types est écrite dans le `.tlh` fichier avec le code généré par attribut conservé.

## <a name="syntax"></a>Syntaxe

> **#import** *de la bibliothèque de types* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>Paramètres

**emitidl**\
Les informations de type importées à partir de la *bibliothèque de types* sont présentes dans le IDL généré pour le projet avec attributs. Ce comportement est le comportement par défaut et est appliqué si vous ne spécifiez pas de paramètre pour `embedded_idl` .

**« no_emitidl »**\
Les informations de type importées à partir de la *bibliothèque de types* ne sont pas présentes dans le IDL généré pour le projet avec attributs.

## <a name="example"></a>Exemple

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
