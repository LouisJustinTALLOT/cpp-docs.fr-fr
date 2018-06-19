---
title: Erreur du compilateur C2865 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246214"
---
# <a name="compiler-error-c2865"></a>Erreur du compilateur C2865
'fonction' : comparaison non conforme pour handle_ou_pointeur  
  
 Vous pouvez comparer les références aux [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md) ou gestion des types de référence uniquement pour l’égalité pour voir s’ils font référence au même objet (==) ou à des objets différents ( ! =).  
  
 Impossible de comparer les pour le classement car le runtime .NET peut déplacer des objets managés à tout moment, modifier le résultat du test.