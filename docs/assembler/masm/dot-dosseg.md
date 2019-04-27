---
title: .DOSSEG
ms.date: 08/30/2018
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 28b3e351030ee83693c0fec5568aacf9b4b77c27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204359"
---
# <a name="dosseg"></a>.DOSSEG

Les segments conformément à la convention de segment MS-DOS des commandes : CODE first, puis DGROUP de segments et puis segments dans DGROUP.

## <a name="syntax"></a>Syntaxe

> .DOSSEG

## <a name="remarks"></a>Notes

Les segments dans DGROUP suivent cet ordre : segments hors BSS ou de la pile, les segments BSS et segments de pile. Principalement utilisé pour garantir la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>