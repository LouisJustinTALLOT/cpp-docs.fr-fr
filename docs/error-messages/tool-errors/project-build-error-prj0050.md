---
title: PRJ0050 d’erreur de Build de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad17614f693e313190dba9cc767c023981dec34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318511"
---
# <a name="project-build-error-prj0050"></a>Erreur de génération de projet PRJ0050
Échec de l’inscription de la sortie. Vérifiez que vous disposez des autorisations appropriées pour modifier le Registre.  
  
 Le système de génération Visual C++ n’a pas pu enregistrer la sortie de la build (dll ou .exe). Vous devez avoir ouvert une session en tant qu’administrateur pour modifier le Registre.  
  
 Si vous générez un fichier .dll, vous pouvez essayer d’inscrire le fichier .dll manuellement à l’aide de regsvr32.exe, il doit afficher des informations sur la raison pour laquelle la génération a échoué.  
  
 Si vous ne créez pas un fichier .dll, examinez le journal de génération de la commande qui provoque une erreur.