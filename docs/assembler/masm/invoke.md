---
title: INVOKE
ms.date: 08/30/2018
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: efa8f710701e15845c3a6a22ba024c9cf1882457
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202616"
---
# <a name="invoke"></a>INVOKE

Appelle la procédure à l’adresse indiquée par *expression*, en transmettant les arguments sur la pile ou dans les registres selon les conventions d’appel standards du type de langage.

## <a name="syntax"></a>Syntaxe

> INVOKE *expression* [[, *arguments*]]

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (précédé d’une expression `ADDR`).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>