---
title: Erreur RC2101 du compilateur de ressources | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2101
dev_langs: C++
helpviewer_keywords: RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d08e9ddb7b8cda127b1d05bfef52b52833534cb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2101"></a>Erreur RC2101 du compilateur de ressources 
Directive non valide dans le fichier RC prétraité  
  
 Le fichier du compilateur de ressources contient un **#pragma** directive.  
  
 Utilisez le **#ifndef** directive de préprocesseur avec la constante RC_INVOKED définie par le compilateur de ressources lorsqu’il traite un fichier include. Place le **#pragma** directive à l’intérieur d’un bloc de code qui n’est pas traité lorsque la constante RC_INVOKED est définie. Le code dans le bloc est traité exclusivement par le compilateur C/C++ et non par le compilateur de ressources. L’exemple de code suivant illustre cette technique :  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 Le **#pragma** directive de préprocesseur n’a aucune signification un. Fichier RC. Le **#include** directive de préprocesseur est fréquemment utilisée dans un. Fichier RC pour inclure un fichier d’en-tête (un fichier d’en-tête de personnalisée basée sur le projet ou un fichier d’en-tête standard fourni par Microsoft avec l’un de ses produits). Certains de ces fichiers include contiennent la **#pragma** directive. Un fichier d’en-tête peut contenir un ou plusieurs autres fichiers d’en-tête, le fichier qui contient l’incriminée **#pragma** directive ne peut pas être évidente.  
  
 Le **#ifndef** RC_INVOKED peut contrôler, y compris les fichiers d’en-tête dans les fichiers d’en-tête de projet.