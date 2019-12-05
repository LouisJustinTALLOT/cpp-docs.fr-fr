---
title: Erreur ML non fatale A2066
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 8dc3000b2edc2b1ecda7cc3952b554296de19aa3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855877"
---
# <a name="ml-nonfatal-error-a2066"></a>Erreur ML non fatale A2066

**mode UC et taille de segment incompatibles**

Une tentative a été faite pour ouvrir un segment avec un attribut **USE16**, **USE32**ou **Flat** qui n’était pas compatible avec l’UC spécifiée, ou pour basculer vers un processeur 16 bits alors qu’il se trouve dans un segment 32 bits.

Les attributs **USE32** et **Flat** doivent être précédés de la directive de processeur. 386 ou d’une version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>