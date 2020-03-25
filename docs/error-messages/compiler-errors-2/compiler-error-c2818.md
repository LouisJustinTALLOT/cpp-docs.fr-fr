---
title: Erreur du compilateur C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202107"
---
# <a name="compiler-error-c2818"></a>Erreur du compilateur C2818

l’application de’operator-> 'surchargé est récursive à travers le type’type'

Une redéfinition de l’opérateur d’accès aux membres de la classe contient une instruction `return` récursive. Pour redéfinir l’opérateur `->` avec la récursivité, vous devez déplacer la routine récursive vers une fonction distincte appelée à partir de la fonction de substitution d’opérateur.
