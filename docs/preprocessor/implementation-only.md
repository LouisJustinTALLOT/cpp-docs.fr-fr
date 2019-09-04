---
title: implementation_only importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218974"
---
# <a name="implementation_only-import-attribute"></a>implementation_only importer l’attribut

**C++Plus**

Supprime la génération du fichier d' `.tlh` en-tête de la bibliothèque de types principale.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **implementation_only**

## <a name="remarks"></a>Notes

Ce fichier contient toutes les déclarations utilisées pour exposer le contenu de la bibliothèque de types. Le `.tli` fichier d’en-tête, avec les implémentations des fonctions membres Wrapper, sera généré et inclus dans la compilation.

Lorsque cet attribut est spécifié, le contenu de l' `.tli` en-tête se trouve dans le même espace de noms que celui `.tlh` normalement utilisé dans l’en-tête. En outre, les fonctions membres ne sont pas déclarées comme inline.

L’attribut **implementation_only** est destiné à être utilisé conjointement avec l’attribut [no_implementation](../preprocessor/no-implementation.md) pour la conservation des implémentations du fichier d’en-tête précompilé (PCH). Une instruction `#import` avec l’attribut `no_implementation` est placée dans la région source utilisée pour créer le PCH. Le PCH résultant est utilisé par plusieurs fichiers sources. Une `#import` instruction avec l’attribut **implementation_only** est ensuite utilisée en dehors de la région pch. Vous ne devez utiliser cette instruction qu’une seule fois dans l’un des fichiers sources. Il génère toutes les fonctions membres de wrapper requises sans recompilation supplémentaire pour chaque fichier source.

> [!NOTE]
> L’attribut **implementation_only** dans une `#import` instruction doit être utilisé conjointement avec une autre `#import` instruction, de la même bibliothèque de types, avec `no_implementation` l’attribut. Dans le cas contraire, des erreurs de compilation sont générées. Cela est dû au fait que les définitions de `#import` classe wrapper générées par l’instruction avec l' `no_implementation` attribut sont requises pour compiler les implémentations générées par l’attribut **implementation_only** .

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
