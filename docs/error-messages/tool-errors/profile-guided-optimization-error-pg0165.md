---
title: PG0165 d’erreur de l’optimisation guidée par profil | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084209"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Erreur de l'optimisation guidée par profil PG0165

Lecture de 'Nomfichier.PGD' : ' version PGD n’est pas pris en charge (incompatibilité de version)'.

Les fichiers PGD sont spécifiques à un ensemble d’outils du compilateur particulier. Cette erreur est générée lorsque vous utilisez un compilateur autre que celui utilisé pour *Filename*.pgd. Cette erreur indique que cet ensemble d’outils du compilateur ne peut pas utiliser les données à partir de *Filename*.pgd pour optimiser le programme en cours.

Pour résoudre ce problème, régénérez *Filename*.pgd à l’aide de l’ensemble d’outils du compilateur actuel.