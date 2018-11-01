---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596870"
---
# <a name="local-masm"></a>LOCAL (MASM)

Dans la première directive, au sein d’une macro, **LOCAL** définit les étiquettes qui sont uniques à chaque instance de la macro.

## <a name="syntax"></a>Syntaxe

> LOCAL *localname* [[, *localname*]]...

> LOCAL *étiquette* [[[*nombre*]]] [[ :*type*]] [[, *étiquette* [[[*nombre*]]] [[ *type*]]]]...

## <a name="remarks"></a>Notes

Dans la deuxième directive, au sein d’une définition de procédure (**PROC**), **LOCAL** crée des variables de pile qui existent pendant la durée de la procédure. Le *étiquette* peut être une simple variable ou un tableau contenant *nombre* éléments.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>