---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2066'
title: Erreur ML non fatale A2066
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2066
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
ms.openlocfilehash: 703244bde7b55a5e109352a3e51a0b4402829242
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128750"
---
# <a name="ml-nonfatal-error-a2066"></a>Erreur ML non fatale A2066

**mode UC et taille de segment incompatibles**

Une tentative a été faite pour ouvrir un segment avec un attribut **USE16**, **USE32** ou **Flat** qui n’était pas compatible avec l’UC spécifiée, ou pour basculer vers un processeur 16 bits alors qu’il se trouve dans un segment 32 bits.

Les attributs **USE32** et **Flat** doivent être précédés de la directive de processeur. 386 ou d’une version ultérieure.

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
