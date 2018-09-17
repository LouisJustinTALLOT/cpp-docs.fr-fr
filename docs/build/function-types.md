---
title: Types de fonctions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dfb36dc9e177fdb9ad196c0e2a8ad0f352d5f2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709564"
---
# <a name="function-types"></a>Types de fonctions

Il existe essentiellement deux types de fonctions. Une fonction qui nécessite un frame de pile est appelée une fonction de frame. Une fonction qui ne nécessite pas d’un frame de pile est appelée une fonction de la feuille.

Une fonction de frame est une fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions. Elle requiert également une entrée de table de fonction. Une fonction de frame exige un prologue et un épilogue. Une fonction de frame peut allouer dynamiquement de l’espace de pile et pouvez employer un pointeur de frame. Une fonction de frame a toutes les fonctionnalités de cet appel standard à sa disposition.

Si une fonction de frame n’appelle pas une autre fonction, il n’est pas nécessaire d’aligner la pile (référencé dans la Section [Allocation de piles](../build/stack-allocation.md)).

Une feuille est une fonction qui ne nécessite pas une entrée de table de fonction. Il ne peut pas apporter des modifications pour les registres non volatils, y compris RSP, ce qui signifie qu’il ne peut pas appeler des fonctions ou allouer de l’espace de pile. Il est autorisé à laisser la pile non alignés lors de son exécution.

## <a name="see-also"></a>Voir aussi

[Utilisation de la pile](../build/stack-usage.md)
