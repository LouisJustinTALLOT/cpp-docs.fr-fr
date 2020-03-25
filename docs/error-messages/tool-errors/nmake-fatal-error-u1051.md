---
title: Erreur irrécupérable NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193678"
---
# <a name="nmake-fatal-error-u1051"></a>Erreur irrécupérable NMAKE U1051

mémoire insuffisante

NMAKE ne dispose pas de suffisamment de mémoire, y compris la mémoire virtuelle, car le Makefile était trop grand ou complexe.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace sur le disque.

1. Augmentez la taille du fichier d’échange Windows NT ou du fichier d’échange Windows.

1. Si seule une partie du Makefile est utilisée, divisez le Makefile en fichiers distincts ou utilisez **! Si** les directives de prétraitement limitent la quantité que doit traiter NMAKE. Le **! Si** les directives incluent **! Si**, `!IFDEF`, **! IFNDEF**, **! Sinon, si**, **! SINON** `IFDEF`, et **! SINON** `IFNDEF`.
