---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4799'
title: Avertissement du compilateur (niveau 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 9bfa84791a713d5ed5c0382402b958c255e30521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334936"
---
# <a name="compiler-warning-level-1-c4799"></a>Avertissement du compilateur (niveau 1) C4799

> Aucun EMMS à la fin de la fonction'*Function*'

La fonction a au moins une instruction MMX, mais elle n’a pas d' `EMMS` instruction. Lorsqu’une instruction multimédia est utilisée, une `EMMS` instruction ou `_mm_empty` intrinsèque doit également être utilisé pour effacer le mot de balise multimédia à la fin du code MMX.

Vous pouvez recevoir C4799 lors de l’utilisation de ivec. h, indiquant que le code n’utilise pas correctement l’instruction EMMS avant de retourner. Il s’agit d’un faux Avertissement pour ces en-têtes. Vous pouvez les désactiver en définissant _SILENCE_IVEC_C4799 dans ivec. h. Toutefois, sachez que cela empêchera également le compilateur de donner des avertissements corrects de ce type.

Pour obtenir des informations connexes, consultez le [jeu d’instructions MMX d’Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
