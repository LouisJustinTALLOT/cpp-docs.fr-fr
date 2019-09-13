---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927726"
---
# <a name="disasm"></a>/DISASM

Imprimez le désassemblage des sections de code dans la sortie DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/DISASM** { **:** \[**OCTETS**NOOCTETS]}|

### <a name="arguments"></a>Arguments

**BITS**<br/>
Comprend les octets d’instruction ainsi que les OpCodes et les arguments interprétés dans la sortie du code machine. Il s'agit de l'option par défaut.

**NOOCTETS**<br/>
N’inclut pas les octets d’instruction dans la sortie du code machine.

## <a name="remarks"></a>Notes

L’option **/DISASM** affiche le code machine des sections de code dans le fichier. Il utilise des symboles de débogage s’ils sont présents dans le fichier.

**/DISASM** doit être utilisé uniquement sur les images natives, non managées. L’outil équivalent pour le code managé est [Ildasm](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Seule l’option [/headers](headers.md) DUMPBIN peut être utilisée sur les fichiers générés par l’option du compilateur [/GL (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md) .

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
