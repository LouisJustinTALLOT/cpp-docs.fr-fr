---
title: Erreur de l'optimisation guidée par profil PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359733"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Erreur de l'optimisation guidée par profil PG0165

Lecture de 'Nomfichier.PGD' : « Version PGD n’est pas pris en charge (incompatibilité de version)'.

Les fichiers PGD sont spécifiques à un ensemble d’outils du compilateur particulier. Cette erreur est générée lorsque vous utilisez un compilateur autre que celui utilisé pour *Filename*.pgd. Cette erreur indique que cet ensemble d’outils du compilateur ne peut pas utiliser les données à partir de *Filename*.pgd pour optimiser le programme en cours.

Pour résoudre ce problème, régénérez *Filename*.pgd à l’aide de l’ensemble d’outils du compilateur actuel.