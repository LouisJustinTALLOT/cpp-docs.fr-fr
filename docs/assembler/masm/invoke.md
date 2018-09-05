---
title: APPELER | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5698acf9986903a1d6d731c1047484a0ce6904
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676515"
---
# <a name="invoke"></a>INVOKE

Appelle la procédure à l’adresse indiquée par *expression*, en transmettant les arguments sur la pile ou dans les registres selon les conventions d’appel standards du type de langage.

## <a name="syntax"></a>Syntaxe

> INVOKE *expression* [[, *arguments*]]

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (précédé d’une expression `ADDR`).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>