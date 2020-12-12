---
description: En savoir plus sur:/DISASM
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 764754e017958a57afd53236b7fc1ffb6217d850
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192900"
---
# <a name="disasm"></a>/DISASM

Imprimez le désassemblage des sections de code dans la sortie DUMPBIN.

## <a name="syntax"></a>Syntaxe

> **/DISASM**{**:** \[ **octets** | **nooctets**]}

### <a name="arguments"></a>Arguments

**BITS**<br/>
Comprend les octets d’instruction ainsi que les OpCodes et les arguments interprétés dans la sortie du code machine. Il s'agit de l'option par défaut.

**Nooctets**<br/>
N’inclut pas les octets d’instruction dans la sortie du code machine.

## <a name="remarks"></a>Notes

L’option **/DISASM** affiche le code machine des sections de code dans le fichier. Il utilise des symboles de débogage s’ils sont présents dans le fichier.

**/DISASM** doit être utilisé uniquement sur les images natives, non managées. L’outil équivalent pour le code managé est [Ildasm](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Seule l’option [/headers](headers.md) DUMPBIN peut être utilisée sur les fichiers générés par l’option du compilateur [/GL (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md) .

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
