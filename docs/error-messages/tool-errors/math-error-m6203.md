---
description: 'En savoir plus sur : erreur mathématique mathématique M6203'
title: Erreur mathématique M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: fcb123af8c79b5ce839e13247f59cbbed42736f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143869"
---
# <a name="math-error-m6203"></a>Erreur mathématique M6203

'fonction' : erreur _OVERFLOW

Le résultat de fonction donné était trop grand pour être représenté.

Cette erreur appelle la `_matherr` fonction avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.
