---
title: exclure (#import) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c345d9268f63a714eeae4beff78a7ac39ce545a1
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807898"
---
# <a name="exclude-import"></a>exclure (\#importer)

**Spécifique à C++**

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

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. Cet attribut peut prendre un nombre quelconque d’arguments, chacun étant un élément de niveau supérieur de bibliothèque de types à exclure.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)