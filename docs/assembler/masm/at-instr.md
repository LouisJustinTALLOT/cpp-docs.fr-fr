---
title: '@InStr | Microsoft Docs'
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- '@InStr'
dev_langs:
- C++
helpviewer_keywords:
- '@InStr symbol'
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0beb5fbde4433ad436d9dffa0dd3048b17a7fcd
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682991"
---
# <a name="instr"></a>@InStr

Fonction de macro qui recherche la première occurrence de *string2* dans *string1*, en commençant par *position* dans *string1*. Si *position* n’apparaît pas, la recherche commence au début de *string1*. Retourne un entier de position ou 0 si *string2* est introuvable.

## <a name="syntax"></a>Syntaxe

> @InStr([[positionner]], chaîne1, chaîne2)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les symboles](../../assembler/masm/symbols-reference.md)<br/>