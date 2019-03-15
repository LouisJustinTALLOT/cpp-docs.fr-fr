---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822533"
---
# <a name="disasm"></a>/DISASM

Imprimer le code machine des sections de code dans la sortie DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/ DISASM**{**:**\[**OCTETS**|**NOBYTES**]}

### <a name="arguments"></a>Arguments

**OCTETS**<br/>
Inclut les octets de l’instruction avec les opcodes interprétées et les arguments dans la sortie du code machine. Il s'agit de l'option par défaut.

**NOBYTES**<br/>
N’inclut pas les octets de l’instruction dans la sortie du code machine.

## <a name="remarks"></a>Notes

Le **/DISASM** option affiche le code machine des sections de code dans le fichier. Il utilise les symboles de débogage s’ils sont présents dans le fichier.

**/ DISASM** doit uniquement être utilisée sur des images natives, non gérés,. L’outil équivalent pour le code managé est [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Uniquement les [/HEADERS](headers.md) (option DUMPBIN) est disponible pour les fichiers générés par le [/GL (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
