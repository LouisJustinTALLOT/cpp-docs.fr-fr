---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2096'
title: Erreur ML non fatale A2096
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: cbef33a8147b9f4cbe436860611f643b4f272516
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128529"
---
# <a name="ml-nonfatal-error-a2096"></a>Erreur ML non fatale A2096

**Registre de segment, de groupe ou de segment ATTENDU**

Un segment ou un groupe était attendu mais n’a pas été trouvé.

L’un des éléments suivants s’est produit :

- L’opérande gauche spécifié avec l’opérateur de substitution de segment (**:**) n’est pas un registre de segment (CS, DS, SS, ES, FS ou GS), un nom de groupe, un nom de segment ou une expression de segment.

- La directive [supposer](assume.md) a reçu un registre de segment sans adresse de segment valide, registre de segment, groupe ou groupe **plat** spécial.

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
