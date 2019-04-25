---
title: 'Erreur RC2151 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173442"
---
# <a name="resource-compiler-error-rc2151"></a>Erreur RC2151 du compilateur de ressources 

Impossible de réutiliser les constantes de chaînes

À l’aide de la même valeur à deux reprises dans un **STRINGTABLE** instruction. Assurez-vous que vous n’utilisez pas plusieurs chevauchement des valeurs décimales et hexadécimales.

Chaque ID d’un **STRINGTABLE** doit être unique. Pour une efficacité maximale utilisez des constantes contiguës qui démarrent sur un multiple de 16.