---
title: Opérateurs de préprocesseur
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 5dd252fb495a05efe6eef45674f9ecd601a298a7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857942"
---
# <a name="preprocessor-operators"></a>Opérateurs de préprocesseur

Quatre opérateurs propres au préprocesseur sont utilisés dans le contexte de la directive `#define`. Consultez le tableau suivant pour obtenir un résumé de chacun d’entre eux. Les opérateurs de chaînement, de création de caractères et de collage de jeton sont présentés dans les trois sections suivantes. Pour plus d’informations sur l’opérateur `defined`, consultez [les directives #if, #elif, #else et #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|opérateur|Action|
|--------------|------------|
|[Opérateur de chaîne (#)](../preprocessor/stringizing-operator-hash.md)|Fait figurer l’argument réel correspondant entre guillemets doubles|
|[Opérateur de caractères (# @)](../preprocessor/charizing-operator-hash-at.md)|Indique que l’argument correspondant doit être entouré de guillemets simples et qu’il doit être traité comme un caractère (spécifique à Microsoft)|
|[Opérateur de collage de jeton (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|Autorise la concaténation des jetons utilisés comme arguments réels pour former d’autres jetons|
|[opérateur défini](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifie l’écriture d’expressions composées dans certaines directives de macro|

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)\
[Macros prédéfinies](../preprocessor/predefined-macros.md)\
[Référence du préprocesseur c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
