---
title: Erreur ML non fatale A2066
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 4c7c32264fe5daa6cd4e14f47cff111899e8f8d6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316887"
---
# <a name="ml-nonfatal-error-a2066"></a>Erreur ML non fatale A2066

**mode UC et taille de segment incompatibles**

Une tentative a été faite pour ouvrir un segment avec un attribut **USE16**, **USE32**ou **Flat** qui n’était pas compatible avec l’UC spécifiée, ou pour basculer vers un processeur 16 bits alors qu’il se trouve dans un segment 32 bits.

Les attributs **USE32** et **Flat** doivent être précédés de la directive de processeur. 386 ou d’une version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
