---
title: /DISASM | Documents Microsoft
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /disasm
dev_langs:
- C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89b0784ff10e7d9521351e01d8907c963c9304fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370369"
---
# <a name="disasm"></a>/DISASM

Imprimer le code machine des sections de code dans la sortie DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/ DISASM**{**:**\[**OCTETS**|**NOBYTES**]}  

### <a name="arguments"></a>Arguments

**OCTETS**  
Inclut les octets de l’instruction avec les opcodes interprétées et les arguments dans la sortie du code machine. Il s'agit de l'option par défaut.

**NOBYTES**  
N’inclut pas les octets de l’instruction dans la sortie du code machine.

## <a name="remarks"></a>Notes

Le **/DISASM** option affiche le code machine des sections de code dans le fichier. Il utilise les symboles de débogage s’ils sont présents dans le fichier.

**/DISASM** doit uniquement être utilisée sur des images natives non managés,. L’outil équivalent pour le code managé est [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés par le [/GL (optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)  
