---
title: Erreur irrécupérable NMAKE U1059 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320701"
---
# <a name="nmake-fatal-error-u1059"></a>Erreur irrécupérable NMAKE U1059
Erreur de syntaxe : '}' manquant dans le fichier dépendant  
  
 Un chemin de recherche pour une dépendance a été incorrectement spécifié. Soit un espace se trouvait dans le chemin d’accès ou l’accolade fermante (**}**) a été omis.  
  
 La syntaxe pour une spécification de répertoire d’un dépendant est  
  
 **{**   
 ***répertoires* } dépendant**  
  
 où `directories` spécifie un ou plusieurs chemins d’accès, chacun étant séparés par un point-virgule (**;**). Aucun des espaces ne sont autorisés.  
  
 Si tout ou partie d’un chemin de recherche est remplacé par une macro, assurez-vous que sans espaces existent dans l’expansion macro.