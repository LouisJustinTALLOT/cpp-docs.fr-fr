---
title: Erreur du compilateur C2667 | Documents Microsoft
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
ms.openlocfilehash: f5458bc5dc9500ea7850833b073d40d66bfc6e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232354"
---
# <a name="compiler-error-c2667"></a>Erreur du compilateur C2667
'fonction' : aucune des surcharges nombre ont une meilleure conversion  
  
 Un appel de fonction surchargée est ambigu et ne peut pas être résolu.  
  
 La conversion nécessaire pour faire correspondre les paramètres réels dans l’appel de fonction à une des fonctions surchargées doit impérativement être meilleure que les conversions requises par toutes les autres fonctions surchargées.  
  
 Consultez l’article Q240869 de la Base de connaissances Microsoft pour plus d’informations sur le classement partiel des modèles de fonction.