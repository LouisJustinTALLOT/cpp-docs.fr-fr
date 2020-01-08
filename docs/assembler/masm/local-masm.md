---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317147"
---
# <a name="local"></a>LOCAL

Dans la première directive, au sein d’une macro, **local** définit des étiquettes qui sont uniques à chaque instance de la macro.

## <a name="syntax"></a>Syntaxe

> *LocalId* local ⟦, *localId* ... ⟧
>
> **Local** *ID* ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *qualifiedType*⟧ ⟦ __,__ *ID* ⟦ __\[__ *Count* __]__ *⟧ ⟦ qualifiedType*⟧... ⟧

## <a name="remarks"></a>Notes

Dans la deuxième directive, au sein d’une définition de procédure (**proc**), **local** crée des variables basées sur la pile qui existent pour la durée de la procédure. *ID* peut être une variable simple ou un tableau contenant des éléments *Count* , où *Count* est une expression constante.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
