---
title: PRJ0002 d’erreur de Build de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54e1870ce9137ba172f848a499dd31133119eea0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318274"
---
# <a name="project-build-error-prj0002"></a>Erreur de génération de projet PRJ0002
résultat d’erreur retourné à partir de la ligne de commande'.  
  
 Une commande, ***ligne de commande***, ce qui a été formé à partir de l’entrée d’utilisateur dans le **Pages de propriétés** , retourné un code d’erreur, mais aucune information n’apparaît dans la fenêtre Sortie.  
  
 La résolution de cette erreur dépend de l’outil ayant généré l’erreur. Pour MIDL, vous obtenez une idée de la cause du problème si /o (redirection de sortie) est définie.  
  
 Un fichier de commandes, tel qu’une étape de génération personnalisée ou un événement de build, qui n’est pas d’information sur les conditions d’échec peut également être la raison de cette erreur.