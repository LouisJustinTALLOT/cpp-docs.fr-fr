---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: cf7d06eddb5ae6d08f57fb82613d97c7dcc36074
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566710"
---
# <a name="injectstatement"></a>inject_statement

**Spécifique à C++**

Insère son argument en tant que texte source dans l’en-tête de bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```
inject_statement("source_text")
```

### <a name="parameters"></a>Paramètres

*source_text*<br/>
Texte source à insérer dans le fichier d'en-tête de bibliothèque de types.

## <a name="remarks"></a>Notes

Le texte est placé au début de la déclaration d'espace de noms qui encapsule le contenu de la bibliothèque de types dans le fichier d'en-tête.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)