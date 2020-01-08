---
title: Erreur ML non fatale A2085
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: f8fdedfc1bc8bff63124d18fe1410d9f144cb926
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316835"
---
# <a name="ml-nonfatal-error-a2085"></a>Erreur ML non fatale A2085

**instruction ou inscription non acceptée en mode UC actuel**

Une tentative d’utilisation d’une instruction, d’un registre ou d’un mot clé qui n’était pas valide pour le mode de processeur actuel a été effectuée.

Par exemple, les registres 32 bits requièrent [. 386](dot-386.md) ou version ultérieure. Les registres de contrôle tels que Registre CR0 nécessitent le mode privilégié [. 386P](dot-386p.md) ou version ultérieure. Cette erreur est également générée pour les mots clés **NEAR32**, **FAR32**et **Flat** , qui requièrent. **386** ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
