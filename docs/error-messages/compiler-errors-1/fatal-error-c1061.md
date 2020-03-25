---
title: Erreur irrécupérable C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 049adb38dd8f33de7dbdd02d8420eba284ca2ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204410"
---
# <a name="fatal-error-c1061"></a>Erreur irrécupérable C1061

limite du compilateur : blocs imbriqués trop profondément

L'imbrication des blocs de code dépasse la limite de 128 niveaux. Il s'agit d'une limite imposée dans le compilateur pour le C et le C++, dans les ensembles d'outils 32 bits et 64 bits. Le nombre de niveaux d'imbrication peut être augmenté par tout ce qui crée une portée ou un bloc. Par exemple, les espaces de noms, les directives using, les expansions de préprocesseur, l'expansion de modèle, la gestion des exceptions, les constructions de boucles et les clauses else-if peuvent augmenter le niveau d'imbrication détecté par le compilateur.

Pour corriger cette erreur, vous devez refactoriser votre code. Dans tous les cas, un code profondément imbriqué est difficile à comprendre et à analyser. Si vous refactorisez votre code afin qu'il comporte moins de niveaux d'imbrication, cela peut améliorer sa qualité et simplifier sa maintenance. Décomposez le code profondément imbriqué en fonctions qui sont appelées à partir du contexte d'origine. Limitez le nombre de boucles ou de clauses else-if chaînées dans un bloc.
