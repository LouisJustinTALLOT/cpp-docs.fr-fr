---
title: Erreur irrécupérable C1061 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1061
dev_langs:
- C++
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fde2d3a076b4cf78a8104fd19719bec205828c68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225700"
---
# <a name="fatal-error-c1061"></a>Erreur irrécupérable C1061
limite du compilateur : blocs imbriqués trop profondément  
  
 L'imbrication des blocs de code dépasse la limite de 128 niveaux. Il s'agit d'une limite imposée dans le compilateur pour le C et le C++, dans les ensembles d'outils 32 bits et 64 bits. Le nombre de niveaux d'imbrication peut être augmenté par tout ce qui crée une portée ou un bloc. Par exemple, les espaces de noms, les directives using, les expansions de préprocesseur, l'expansion de modèle, la gestion des exceptions, les constructions de boucles et les clauses else-if peuvent augmenter le niveau d'imbrication détecté par le compilateur.  
  
 Pour corriger cette erreur, vous devez refactoriser votre code. Dans tous les cas, un code profondément imbriqué est difficile à comprendre et à analyser. Si vous refactorisez votre code afin qu'il comporte moins de niveaux d'imbrication, cela peut améliorer sa qualité et simplifier sa maintenance. Décomposez le code profondément imbriqué en fonctions qui sont appelées à partir du contexte d'origine. Limitez le nombre de boucles ou de clauses else-if chaînées dans un bloc.