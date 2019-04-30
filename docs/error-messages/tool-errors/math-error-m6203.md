---
title: Erreur mathématique M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 4433a024d461ee1bc43aa5fa82344190377243b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400771"
---
# <a name="math-error-m6203"></a>Erreur mathématique M6203

'fonction' : erreur _OVERFLOW

Le résultat de la fonction donnée était trop grand pour être représenté.

Cette erreur appelle le `_matherr` fonction avec le nom de fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction permettant de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.