---
title: Compilateur avertissement (niveau 1) C4041 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd8c933522e523329c41ebe666a5a7e3c198cb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286095"
---
# <a name="compiler-warning-level-1-c4041"></a>Avertissement du compilateur (niveau 1) C4041
limite du compilateur : arrêt de la sortie de l’explorateur  
  
 Les informations du navigateur dépassent la limite du compilateur.  
  
 Cet avertissement peut être dû à une compilation avec [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informations du navigateur comprenant des variables locales).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Compilez avec /Fr (informations du navigateur sans variables locales).  
  
2.  Désactivez la sortie de navigateur (compilez sans /FR ou /Fr).