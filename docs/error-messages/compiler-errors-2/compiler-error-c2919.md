---
description: 'En savoir plus sur : erreur du compilateur C2919'
title: Erreur du compilateur C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: 0e6498961fc5000897bcd9815c3cd3a6f90ecdfb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270340"
---
# <a name="compiler-error-c2919"></a>Erreur du compilateur C2919

'type' : les opérateurs ne peuvent pas être utilisés sur la surface publiée d'un type WinRT

Le système de type Windows Runtime ne prend pas en charge les fonctions membres d'opérateur dans la surface publiée d'un type. Cela est dû au fait que tous les langages ne peuvent pas consommer les fonctions membres d'opérateur. Vous pouvez créer des fonctions membres d'opérateur privé ou interne qui peuvent être appelées à partir du code C++ dans la même unité de compilation ou de classe.

Pour résoudre ce problème, supprimez la fonction membre de l'opérateur à partir de l'interface publique, ou remplacez-la par une fonction membre nommée. Par exemple, à la place de `operator==`, nommez la fonction membre `Equals`.
