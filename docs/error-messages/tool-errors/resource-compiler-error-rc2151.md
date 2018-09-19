---
title: Erreur RC2151 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109780"
---
# <a name="resource-compiler-error-rc2151"></a>Erreur RC2151 du compilateur de ressources 

Impossible de réutiliser les constantes de chaînes

À l’aide de la même valeur à deux reprises dans un **STRINGTABLE** instruction. Assurez-vous que vous n’utilisez pas plusieurs chevauchement des valeurs décimales et hexadécimales.

Chaque ID d’un **STRINGTABLE** doit être unique. Pour une efficacité maximale utilisez des constantes contiguës qui démarrent sur un multiple de 16.