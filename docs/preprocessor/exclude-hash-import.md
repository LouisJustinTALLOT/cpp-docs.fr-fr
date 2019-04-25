---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389318"
---
# <a name="exclude-import"></a>exclude (\#import)

**Spécifique à C++**

Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.

## <a name="syntax"></a>Syntaxe

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>Paramètres

*Name1*<br/>
Premier élément à exclure.

*Name2*<br/>
Deuxième élément à exclure (si nécessaire).

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d'arguments, chacun étant un élément de niveau supérieur de bibliothèque de types à exclure.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)