---
title: Erreur irrécupérable C1001 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f605dd7e4892c4a8b57e544ed857257be72f020d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199026"
---
# <a name="fatal-error-c1001"></a>Erreur irrécupérable C1001

> INTERNE du compilateur ERROR(compiler file *file*, line *number*)  
  
Le compilateur ne peut pas générer de code correct pour une construction, souvent en raison de la combinaison d’une expression et une option d’optimisation ou un problème lors de l’analyse. Si le fichier du compilateur répertorié a une heure utc ou un segment de chemin d’accès de C2, il est probablement une erreur de l’optimisation. Si le fichier a un segment de chemin d’accès cxxfe ou c1xx ou est msc1.cpp, il est probablement une erreur d’analyse. Si le fichier nommé est cl.exe, aucune autre information n’est disponible.  

Vous pouvez souvent résoudre un problème d’optimisation en supprimant une ou plusieurs options d’optimisation. Pour déterminer l’option en cause, supprimez les options une recompilation et l’heure jusqu'à ce que le message d’erreur disparaît. Les options les plus couramment sont [/Og (optimisations globales)](../../build/reference/og-global-optimizations.md) et [/Oi (générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md). Après avoir déterminé l’option d’optimisation est chargée, vous pouvez la désactiver autour de la fonction où l’erreur se produit à l’aide de la [optimiser](../../preprocessor/optimize.md) pragma et continuer à utiliser l’option pour le reste du module. Pour plus d’informations sur les options d’optimisation, consultez [conseillées pour l’optimisation](../../build/reference/optimization-best-practices.md).

Si les optimisations ne sont pas chargées de l’erreur, essayez de réécrire la ligne où l’erreur est signalée, ou plusieurs lignes de code se rapportant à cette ligne. Pour afficher le code de la méthode que le compilateur peut voir après le prétraitement, vous pouvez utiliser la [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) option.

Pour plus d’informations sur la manière d’isoler la source de l’erreur et comment signaler une erreur interne du compilateur à Microsoft, consultez [comment signaler un problème avec l’ensemble d’outils Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).