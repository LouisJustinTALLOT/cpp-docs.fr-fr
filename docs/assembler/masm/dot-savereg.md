---
description: En savoir plus sur :. SAVEREG
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 8b946c9b25c3f4dc6a4696b418e85487e20014eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131181"
---
# <a name="savereg"></a>.SAVEREG

Génère une `UWOP_SAVE_NONVOL` entrée ou un `UWOP_SAVE_NONVOL_FAR` Code de déroulement pour le registre (*reg*) et le décalage (*offset*) spécifiés à l’aide de l’offset de prologue actuel. MASM choisit le codage le plus efficace.

## <a name="syntax"></a>Syntaxe

> **. SAVEREG** *reg*__,__ *décalage*

## <a name="remarks"></a>Notes

**. SAVEREG** permet ml64.exe aux utilisateurs de spécifier la façon dont une fonction Frame se déroule et est uniquement autorisée dans le prologue, qui s’étend de la déclaration d’image [proc](proc.md) à [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata` . **. Les SAVEREG** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
