---
title: Erreur du compilateur C2667 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2667
dev_langs:
- C++
helpviewer_keywords:
- C2667
ms.assetid: 3c91d9d1-18fa-4e0d-a9ba-984d38980ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6d14cf04ae399b10cbaa393d9e9fcc7133f274
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095246"
---
# <a name="compiler-error-c2667"></a>Erreur du compilateur C2667

'fonction' : aucune des surcharges nombre ont une meilleure conversion

Un appel de fonction surchargée est ambigu et ne peut pas être résolu.

La conversion nécessaire pour faire correspondre les paramètres réels dans l’appel de fonction à une des fonctions surchargées doit impérativement être meilleure que les conversions requises par toutes les autres fonctions surchargées.

Consultez l’article Q240869 de la Base de connaissances Microsoft pour plus d’informations sur le classement partiel des modèles de fonction.