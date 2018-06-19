---
title: Erreur irrécupérable NMAKE U1051 | Documents Microsoft
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
ms.openlocfilehash: 570c7e5d8e6e8250a67e4f032ac26b04388cfd00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317412"
---
# <a name="nmake-fatal-error-u1051"></a>Erreur irrécupérable NMAKE U1051
Mémoire insuffisante  
  
 NMAKE a manqué de mémoire, y compris de mémoire virtuelle, car le makefile est trop volumineux ou complexe.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Libérez de l’espace sur le disque.  
  
2.  Augmenter la taille du fichier de pagination de Windows NT ou le fichier d’échange Windows.  
  
3.  Si une partie seulement du makefile est utilisée, divisez le makefile en plusieurs fichiers ou utilisez **! IF** pour limiter la quantité NMAKE doit traiter les directives de prétraitement. Le **! IF** sont les suivantes : **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! AUTRE** `IFDEF`, et **! AUTRE** `IFNDEF`.