---
title: Avertissement BSCMAKE BK4504 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a17aa8b4e2a98d3bda5d21ea84962791b8051dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295182"
---
# <a name="bscmake-warning-bk4504"></a>Avertissement BSCMAKE BK4504
fichier contient trop de références ; en ignorant les références ultérieures provenant de cette source  
  
 Le fichier .cpp contient plus de 64 000 références des symboles. Lorsque BSCMAKE a rencontré des références 64 000 dans un fichier, il ignore toutes les références supplémentaires.  
  
 Pour corriger le problème, fractionnez le fichier en deux ou plusieurs fichiers, chacun d'entre eux ayant moins de 64 000 références de symboles, ou utilisent la `#pragma component(browser)` directive de préprocesseur limite les symboles qui sont générés pour les références particuliers. Pour plus d’informations, consultez [composant](../../preprocessor/component.md).