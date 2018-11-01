---
title: Erreur irrécupérable C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 4ab96c0516ee5593a969669c03ae22f0c211ae27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626122"
---
# <a name="fatal-error-c1383"></a>Erreur irrécupérable C1383

l'option du compilateur /GL est incompatible avec la version installée du Common Language Runtime

L’erreur C1383 se produit quand vous utilisez une version précédente du Common Language Runtime avec un compilateur plus récent et quand vous compilez avec **/clr** et **/GL.**

Pour corriger, n’utilisez pas **/GL** avec **/clr** ou installez la version du Common Language Runtime fournie avec votre compilateur.

Pour plus d’informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) et [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).