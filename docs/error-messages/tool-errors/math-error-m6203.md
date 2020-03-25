---
title: Erreur mathématique M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 371a6c673826c6ce71d7a0eb3b9e08d9488f53f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193691"
---
# <a name="math-error-m6203"></a>Erreur mathématique M6203

'fonction' : erreur _OVERFLOW

Le résultat de fonction donné était trop grand pour être représenté.

Cette erreur appelle la fonction `_matherr` avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la fonction `_matherr` pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.
