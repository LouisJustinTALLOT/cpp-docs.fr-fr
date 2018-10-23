---
title: embedded_idl | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7337595111b01ceeec53cc97f11ec2f35a081c5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808340"
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

- **emitidl**: informations de Type importées à partir du typelib seront présentes dans le fichier IDL généré pour le projet avec attributs.  Il s'agit de la valeur par défaut qui sera appliquée si vous ne spécifiez pas de paramètre pour `embedded_idl`.

- **no_emitidl**: informations de Type importées à partir du typelib ne seront pas présentes dans le fichier IDL généré pour le projet avec attributs.

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