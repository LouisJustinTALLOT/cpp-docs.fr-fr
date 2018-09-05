---
title: EQU | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37509a39d2247649c2971932f402a18f3ac667d4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681305"
---
# <a name="equ"></a>EQU

La première directive affecte la valeur numérique *expression* à *nom*.

## <a name="syntax"></a>Syntaxe

> *nom* EQU *expression*

> *nom* EQU \< *texte*>

## <a name="remarks"></a>Notes

Le *nom* ne peut pas être redéfini plus tard.

Le deuxième affecte la directive spécifié *texte* à *nom*. Le *nom* peuvent être affectés à un autre *texte* plus tard. Consultez [TEXTEQU](../../assembler/masm/textequ.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>