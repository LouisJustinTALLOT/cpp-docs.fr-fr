---
description: 'En savoir plus sur : erreur du compilateur C2818'
title: Erreur du compilateur C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: e258387af290a8070c1c66a56a7523b46482cf99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194785"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818

l’application de’operator-> 'surchargé est récursive à travers le type’type'

Une redéfinition de l’opérateur d’accès aux membres de la classe contient une **`return`** instruction récursive. Pour redéfinir l' `->` opérateur avec la récursivité, vous devez déplacer la routine récursive vers une fonction distincte appelée à partir de la fonction de substitution d’opérateur.
