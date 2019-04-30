---
title: Erreur du compilateur C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388694"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818

application de surchargé 'operator ->' est récurrente à travers le type 'type'

Une redéfinition de l’opérateur de l’accès de membre de classe contient une récursive `return` instruction. Pour redéfinir le `->` opérateur avec la récurrence, vous devez déplacer la routine récursive à une fonction appelée à partir de l’opérateur de substituer la fonction.