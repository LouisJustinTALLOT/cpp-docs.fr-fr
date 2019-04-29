---
title: implementation_only
ms.date: 11/04/2016
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: c1435ca74ac2b5a73c308592b1affe6fca097d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383949"
---
# <a name="implementationonly"></a>implementation_only
**Spécifique à C++**

Supprime la génération du fichier d'en-tête .tlh (fichier d'en-tête principal).

## <a name="syntax"></a>Syntaxe

```
implementation_only
```

## <a name="remarks"></a>Notes

Ce fichier contient toutes les déclarations utilisées pour exposer le contenu de la bibliothèque de types. Le fichier d'en-tête .tli, avec les implémentations des fonctions membres de wrapper, sera généré et inclus dans la compilation.

Lorsque cet attribut est spécifié, le contenu de l'en-tête .tli se trouve dans le même espace de noms que celui utilisé normalement dans l'en-tête .tlh. En outre, les fonctions membres ne sont pas déclarées comme inline.

Le **implementation_only** attribut est destiné à être utilisé conjointement avec le [no_implementation](../preprocessor/no-implementation.md) attribut sous la forme d’un moyen de conserver les implémentations hors du fichier d’en-tête précompilé (PCH). Une instruction `#import` avec l’attribut `no_implementation` est placée dans la région source utilisée pour créer le PCH. Le PCH résultant est utilisé par plusieurs fichiers sources. Un `#import` instruction avec le **implementation_only** attribut est ensuite utilisé en dehors de la zone PCH. Vous ne devez utiliser cette instruction qu'une seule fois dans l'un des fichiers sources. Cela permet de générer toutes les fonctions membres de wrapper requises sans recompilation supplémentaire pour chaque fichier source.

> [!NOTE]
> Le **implementation_only** attribut dans une `#import` instruction doit être utilisé conjointement avec un autre `#import` instruction, de la même bibliothèque de types, avec le `no_implementation` attribut. Sinon, des erreurs du compilateur sont générées. Il s’agit, car les définitions de classe wrapper générées par le `#import` instruction avec le `no_implementation` attribut sont requis pour compiler les implémentations générées par le **implementation_only** attribut.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)