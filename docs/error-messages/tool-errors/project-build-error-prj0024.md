---
title: PRJ0024 d’erreur de Build de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59bf76aba80093bf9e8e653bdfb9fad49687a501
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318345"
---
# <a name="project-build-error-prj0024"></a>Erreur de génération de projet PRJ0024
Chemin de Unicode 'path' n’a pas pu être traduit dans la page de code ANSI de l’utilisateur.  
  
 ***chemin d’accès*** est la version Unicode d’origine de la chaîne de chemin d’accès. Cette erreur peut se produire dans les cas où il existe un chemin Unicode qui ne peut pas être traduit directement en ANSI pour la page de codes système en cours.  
  
 Cette erreur peut se produire si vous travaillez avec un projet qui a été développé sur un système à l’aide d’une page de codes qui n’est pas sur votre ordinateur.  
  
 La résolution de cette erreur est mise à jour le chemin d’accès à utiliser le texte ANSI ou pour installer la page de codes sur votre ordinateur et définissez-le en tant que la valeur par défaut du système.