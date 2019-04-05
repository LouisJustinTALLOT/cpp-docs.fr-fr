---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034285"
---
# <a name="injectstatement"></a>inject_statement

**Section spécifique à C++**

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

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)