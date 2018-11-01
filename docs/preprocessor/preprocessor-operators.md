---
title: Opérateurs de préprocesseur
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 3573ce2d86f38193a4f8f7c1c0f310283f304648
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584390"
---
# <a name="preprocessor-operators"></a>Opérateurs de préprocesseur
Quatre opérateurs propres au préprocesseur sont utilisés dans le contexte de la `#define` directive (voir la liste suivante pour obtenir un résumé de chaque). Les opérateurs de chaîne, de charizing et de collage de jeton sont traités dans les trois sections suivantes. Pour plus d’informations sur la `defined` opérateur, voir [le #if, #elif #else et #endif Directives](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|Opérateur|Action|
|--------------|------------|
|[Opérateur d’enchaînement (#)](../preprocessor/stringizing-operator-hash.md)|Provoque l’argument réel correspondant être placée entre guillemets doubles|
|[Opérateur charizing (#@)](../preprocessor/charizing-operator-hash-at.md)|Provoque l’argument correspondant pour être placée entre guillemets simples et doit être traité comme un caractère (Specific à Microsoft)|
|[Opérateurs de collage de jeton (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Permet les jetons permettant d’être concaténées pour former d’autres jetons en tant qu’arguments réels|
|[opérateur défini](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifie l’écriture des expressions composées dans certaines directives de macro|

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)<br/>
[Macros prédéfinies](../preprocessor/predefined-macros.md)<br/>
[Informations de référence sur le préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)