---
title: LOCAL (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685061"
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