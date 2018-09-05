---
title: ML erreur non fatale A2085 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681434"
---
# <a name="ml-nonfatal-error-a2085"></a>Erreur ML non fatale A2085

**instruction ou register ne pas accepté dans le mode actuel du processeur**

Une tentative a été effectuée d’utiliser une instruction, Registre ou mot clé qui n’était pas valide pour le mode de processeur actuelle.

Par exemple, les registres 32 bits requièrent [.386](../../assembler/masm/dot-386.md) ou version ultérieure. Les registres de contrôle, telles que CR0 nécessiter mode privilégié [.386P](../../assembler/masm/dot-386p.md) ou version ultérieure. Cette erreur sera également générée pour le **NEAR32**, **FAR32**, et **plat** les mots clés, qui nécessitent. **386** ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>