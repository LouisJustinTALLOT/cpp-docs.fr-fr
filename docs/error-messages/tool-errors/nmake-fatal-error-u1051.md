---
title: Erreur irrécupérable NMAKE U1051 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3d3a14b75a30aa22bcc9faafb97a218051bb080
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045014"
---
# <a name="nmake-fatal-error-u1051"></a>Erreur irrécupérable NMAKE U1051

Mémoire insuffisante

NMAKE a manqué de mémoire, y compris la mémoire virtuelle, car le makefile est trop volumineux ou complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace sur le disque.

1. Augmenter la taille de fichier d’échange de Windows NT ou le fichier d’échange Windows.

1. Si une partie seulement du makefile est utilisée, divisez le makefile en fichiers distincts ou utiliser **! IF** pour limiter la quantité NMAKE doit traiter les directives de prétraitement. Le **! IF** sont les suivantes : **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! AUTRE** `IFDEF`, et **! AUTRE** `IFNDEF`.