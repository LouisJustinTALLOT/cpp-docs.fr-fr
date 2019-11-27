---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397257"
---
# <a name="local-masm"></a>LOCAL (MASM)

Dans la première directive, au sein d’une macro, **local** définit des étiquettes qui sont uniques à chaque instance de la macro.

## <a name="syntax"></a>Syntaxe

> **Local** *LocalName* ⟦, *LocalName* ... ⟧
>
> *Nom* local ⟦ __\[__ *nombre* __]__ ⟧ ⟦ __:__ *type*⟧ ⟦ __,__ *étiquette* ⟦ __\[__ *nombre* __]__ ⟧*type*⟦... ⟧

## <a name="remarks"></a>Notes

Dans la deuxième directive, au sein d’une définition de procédure (**proc**), **local** crée des variables basées sur la pile qui existent pour la durée de la procédure. L' *étiquette* peut être une variable simple ou un tableau contenant des éléments *Count* .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
