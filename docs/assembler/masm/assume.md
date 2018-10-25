---
title: SUPPOSONS QUE | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fbba50e56ae06dc3afb64582d4a131bba75a6c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055851"
---
# <a name="assume"></a>ASSUME

Permet la vérification des erreurs pour les valeurs de registres.

## <a name="syntax"></a>Syntaxe

> Prenons *segregister*:*nom* [[, *segregister*:*nom*]]...<br/>
> Prenons *dataregister*:*type* [[, *dataregister*:*type*]]...<br/>
> Prenons *inscrire*: erreur [[, *inscrire*: erreur]]...<br/>
> Supposer que [[*inscrire*:]] rien [[, *inscrire*: rien]]...

## <a name="remarks"></a>Notes

Après un `ASSUME` est mis en effet, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **ERREUR** génère une erreur si le Registre est utilisé. **NOTHING** supprime inscrire la vérification des erreurs. Vous pouvez combiner différents genres d’hypothèses dans une seule instruction.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>