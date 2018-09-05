---
title: . DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693230"
---
# <a name="dosseg"></a>.DOSSEG

Trie les segments conformément à la convention de segment MS-DOS : CODE tout d’abord, puis les segments n’est pas dans DGROUP et segmente ensuite dans DGROUP.

## <a name="syntax"></a>Syntaxe

> .DOSSEG

## <a name="remarks"></a>Notes

Les segments dans DGROUP suivent cet ordre : segments hors BSS ou de la pile, les segments BSS et segments de pile. Principalement utilisé pour garantir la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>