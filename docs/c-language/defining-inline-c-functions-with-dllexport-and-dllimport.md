---
title: "Définition de fonctions inline C avec dllexport et dllimport | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a20ff9e120b8e71536be6a989351df74d2e2c2e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Définition de fonctions inline C avec dllexport et dllimport
**Section spécifique à Microsoft**  
  
 Vous pouvez définir comme inline une fonction avec l'attribut `dllexport`. Dans ce cas, la fonction est toujours instanciée et exportée, qu'elle soit référencée ou non par un module du programme. La fonction est présumée être importée par un autre programme.  
  
 Vous pouvez également définir comme inline une fonction déclarée avec l'attribut **dllimport**. Dans ce cas, la fonction peut être développée (selon la spécification de l’option de compilateur /Ob (inline)) mais jamais instanciée. En particulier, si l'adresse d'une fonction importée inline est reçue, l'adresse de la fonction résidant dans la DLL est retournée. Ce comportement est identique à la réception de l'adresse d'une fonction importée non inline.  
  
 Les données locales statiques et les chaînes des fonctions inline maintiennent les mêmes identités entre la DLL et le client qu'elles le feraient dans un programme unique (c'est-à-dire un fichier exécutable sans interface DLL).  
  
 Soyez vigilant en fournissant des fonctions inline importées. Par exemple, si vous mettez à jour la DLL, ne supposez pas que le client utilisera sa version modifiée. Pour vous assurer que vous chargez la version appropriée de la DLL, régénérez aussi le client de la DLL.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’importation et d’exportation de DLL](../c-language/dll-import-and-export-functions.md)