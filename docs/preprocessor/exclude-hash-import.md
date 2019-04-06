---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032386"
---
# <a name="exclude-import"></a>exclude (\#import)

**Section spécifique à C++**

Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.

## <a name="syntax"></a>Syntaxe

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>Paramètres

*Nom1*<br/>
Premier élément à exclure.

*Name2*<br/>
Deuxième élément à exclure (si nécessaire).

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d'arguments, chacun étant un élément de niveau supérieur de bibliothèque de types à exclure.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)