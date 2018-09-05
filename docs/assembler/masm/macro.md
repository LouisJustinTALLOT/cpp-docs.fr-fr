---
title: MACRO | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MACRO
dev_langs:
- C++
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d957935c9ca91d2d09a093350c8d23a848e58b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688866"
---
# <a name="macro"></a>MACRO

Marque un bloc macro appelé *nom* et établit *paramètre* des espaces réservés pour les arguments transmis lorsque la macro est appelée.

## <a name="syntax"></a>Syntaxe

> *nom* MACRO [[*paramètre* [[ : no | : =*par défaut* | : VARARG]]]]...<br/>
> *Instructions*<br/>
> ENDM [[*valeur*]]

## <a name="remarks"></a>Notes

Retourne une fonction de la macro *valeur* à l’instruction appelante.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>