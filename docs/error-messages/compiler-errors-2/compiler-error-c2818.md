---
title: Erreur du compilateur C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212668"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818

l’application de’operator-> 'surchargé est récursive à travers le type’type'

Une redéfinition de l’opérateur d’accès aux membres de la classe contient une **`return`** instruction récursive. Pour redéfinir l' `->` opérateur avec la récursivité, vous devez déplacer la routine récursive vers une fonction distincte appelée à partir de la fonction de substitution d’opérateur.
