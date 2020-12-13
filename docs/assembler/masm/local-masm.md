---
description: 'En savoir plus sur : LOCAL'
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 27296f69b62de0dcd314b2575f045e06576bbf64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129751"
---
# <a name="local"></a>LOCAL

Dans la première directive, au sein d’une macro, **local** définit des étiquettes qui sont uniques à chaque instance de la macro.

## <a name="syntax"></a>Syntaxe

>  *LocalId* local ⟦, *localId* ... ⟧
>
> **Local** *ID* ⟦ __\[__ *Count*__]__ ⟧ ⟦__:__*qualifiedType*⟧ ⟦__,__ *ID* ⟦ __\[__ *Count*__]__ ⟧ ⟦*qualifiedType*⟧... ⟧

## <a name="remarks"></a>Notes

Dans la deuxième directive, au sein d’une définition de procédure (**proc**), **local** crée des variables basées sur la pile qui existent pour la durée de la procédure. *ID* peut être une variable simple ou un tableau contenant des éléments *Count* , où *Count* est une expression constante.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
