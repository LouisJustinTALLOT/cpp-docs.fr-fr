---
description: 'En savoir plus sur : erreur irrécupérable l’erreur C1047'
title: Erreur irrécupérable C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: e3aa85fb777850ce6ee754ee89b9e351b5eba975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341189"
---
# <a name="fatal-error-c1047"></a>Erreur irrécupérable C1047

Le fichier objet ou le fichier bibliothèque 'fichier' a été créé à l’aide d’un compilateur antérieur à celui d’autres objets ; régénérez les objets et bibliothèques obsolètes

L’erreur C1047 se produit quand des fichiers objets ou des bibliothèques générés à l’aide de la commande **/LTCG** sont liés entre eux, alors qu’ils ont été créés avec des versions différentes de l’ensemble d’outils Visual C++.

Cela peut se produire si vous commencez à utiliser une nouvelle version du compilateur sans avoir effectué de régénération propre des fichiers objets ou des bibliothèques existants.

Pour résoudre l’erreur C1047, régénérez tous les fichiers objets et bibliothèques.
