---
description: 'En savoir plus sur : erreur irrécupérable C1001'
title: Erreur irrécupérable C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: a00e8bc2fe79201f77f67eac6f0756e90eba462b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262826"
---
# <a name="fatal-error-c1001"></a>Erreur irrécupérable C1001

> ERREUR interne du compilateur ( *fichier* du compilateur, *numéro* de ligne)

Le compilateur ne peut pas générer de code correct pour une construction, souvent en raison de la combinaison d’une expression particulière et d’une option d’optimisation, ou d’un problème d’analyse. Si le fichier de compilateur indiqué a un segment de chemin d’accès UTC ou C2, il s’agit probablement d’une erreur d’optimisation. Si le fichier a un segment de chemin d’accès cxxfe ou c1xx, ou est MSc1. cpp, il s’agit probablement d’une erreur d’analyse. Si le fichier nommé est cl.exe, aucune autre information n’est disponible.

Vous pouvez souvent résoudre un problème d’optimisation en supprimant une ou plusieurs options d’optimisation. Pour déterminer l’option en cause, supprimez les options une à la fois et recompilez jusqu’à ce que le message d’erreur soit éloigné. Les options les plus courantes sont les options [/og (optimisations globales)](../../build/reference/og-global-optimizations.md) et [/Oi (générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md). Une fois que vous avez déterminé l’option d’optimisation responsable, vous pouvez la désactiver autour de la fonction dans laquelle l’erreur se produit à l’aide du pragma [optimize](../../preprocessor/optimize.md) , et continuer à utiliser l’option pour le reste du module. Pour plus d’informations sur les options d’optimisation, consultez [meilleures pratiques](../../build/optimization-best-practices.md)pour l’optimisation.

Si les optimisations ne sont pas responsables de l’erreur, essayez de réécrire la ligne où l’erreur est signalée ou plusieurs lignes de code entourant cette ligne. Pour afficher le code de la façon dont le compilateur le voit après le prétraitement, vous pouvez utiliser l’option [/p (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) .

Pour plus d’informations sur la façon d’isoler la source de l’erreur et de signaler une erreur interne du compilateur à Microsoft, consultez [Comment signaler un problème avec l’ensemble d’outils Visual C++](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).
