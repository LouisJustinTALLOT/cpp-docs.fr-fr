---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327601"
---
# <a name="local-masm"></a>LOCAL (MASM)

Dans la première directive, au sein d’une macro, **LOCAL** définit les étiquettes qui sont uniques à chaque instance de la macro.

## <a name="syntax"></a>Syntaxe

> LOCAL *localname* \[, *localname*]...
>
> LOCAL *étiquette* \[ __\[__ *nombre*__]__ ] \[ __:__  *type*] \[ __,__ *étiquette* \[ __\[__ *nombre* __]__  ] \[ *type*]]...

## <a name="remarks"></a>Notes

Dans la deuxième directive, au sein d’une définition de procédure (**PROC**), **LOCAL** crée des variables de pile qui existent pendant la durée de la procédure. Le *étiquette* peut être une simple variable ou un tableau contenant *nombre* éléments.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>