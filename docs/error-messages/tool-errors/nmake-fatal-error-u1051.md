---
title: Erreur irrécupérable NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367198"
---
# <a name="nmake-fatal-error-u1051"></a>Erreur irrécupérable NMAKE U1051

Mémoire insuffisante

NMAKE a manqué de mémoire, y compris la mémoire virtuelle, car le makefile est trop volumineux ou complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace sur le disque.

1. Augmenter la taille de fichier d’échange de Windows NT ou le fichier d’échange Windows.

1. Si une partie seulement du makefile est utilisée, divisez le makefile en fichiers distincts ou utiliser **! IF** pour limiter la quantité NMAKE doit traiter les directives de prétraitement. Le **! IF** sont les suivantes : **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! AUTRE** `IFDEF`, et **! AUTRE** `IFNDEF`.