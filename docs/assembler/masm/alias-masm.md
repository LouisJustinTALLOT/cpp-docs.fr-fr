---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 274ac451005015b2693d8674673af574ec781bdc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399293"
---
# <a name="alias-masm"></a>ALIAS (MASM)

The **ALIAS** directive creates an alternate name for a function.  This lets you create multiple names for a function, or create libraries that allow the linker (LINK.exe) to map an old function to a new function.

## <a name="syntax"></a>Syntaxe

> **ALIAS \<** _alias_ **> = \<** _actual-name_ **>**

#### <a name="parameters"></a>Paramètres

*actual-name*\
The actual name of the function or procedure.  The angle brackets are required.

*alias*\
The alternate or alias name.  The angle brackets are required.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
