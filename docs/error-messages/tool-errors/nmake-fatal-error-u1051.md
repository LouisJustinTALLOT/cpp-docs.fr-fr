---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1051'
title: Erreur irrécupérable NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: c7d465eaf34adb69e41f523006fb0740eea722ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272108"
---
# <a name="nmake-fatal-error-u1051"></a>Erreur irrécupérable NMAKE U1051

mémoire insuffisante

NMAKE ne dispose pas de suffisamment de mémoire, y compris la mémoire virtuelle, car le Makefile était trop grand ou complexe.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace sur le disque.

1. Augmentez la taille du fichier d’échange Windows NT ou du fichier d’échange Windows.

1. Si seule une partie du Makefile est utilisée, divisez le Makefile en fichiers distincts ou utilisez **! Si** les directives de prétraitement limitent la quantité que doit traiter NMAKE. Le **! Si** les directives incluent **! Si**, `!IFDEF` , **! IFNDEF**, **! Sinon, si**, **! SINON** `IFDEF` , et **! SINON** `IFNDEF` .
