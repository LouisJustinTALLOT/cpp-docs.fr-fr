---
title: "Fonction main et exécution du programme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9967481734c49d40d3121f825783b1824ad6f4f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="main-function-and-program-execution"></a>Fonction main et exécution du programme
Chaque programme C possède une fonction principale (main) qui doit être nommée **main**. Si votre code suit le modèle de programmation Unicode, vous pouvez utiliser la version de **main** avec les caractères larges, soit **wmain**. La fonction **main** sert de point de départ à l'exécution du programme. Elle contrôle généralement l'exécution du programme en dirigeant les appels à d'autres fonctions du programme. L'exécution d'un programme s'arrête habituellement à la fin de **main** bien qu'elle puisse se terminer à d'autres points du programme pour diverses raisons. Parfois, par exemple lorsqu'une erreur d'un certain type est détectée, vous pouvez forcer l'arrêt d'un programme. Pour cela, utilisez la fonction **exit**. Consultez *Références sur les bibliothèques Runtime C* pour plus d'informations sur l'utilisation de la fonction [exit](../c-runtime-library/reference/exit-exit-exit.md) et pour obtenir un exemple d'utilisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
main( int argc, char *argv[ ], char *envp[ ] )  
```  
  
## <a name="remarks"></a>Notes  
 Les fonctions du programme source effectuent une ou plusieurs tâches spécifiques. La fonction **main** peut appeler ces fonctions afin qu’elles effectuent leurs tâches respectives. Lorsque **main** appelle une autre fonction, elle passe le contrôle d'exécution à cette fonction afin que l'exécution commence à la première instruction de cette fonction. Une fonction retourne le contrôle à **main** lorsqu'une instruction `return` est exécutée ou que la fin de la fonction est atteinte.  
  
 Vous pouvez déclarer toute fonction, notamment **main**, pour avoir des paramètres. Le terme « paramètre » ou « paramètre formel » désigne l'identificateur qui reçoit une valeur passée à une fonction. Pour plus d’informations sur la transmission d’arguments aux paramètres, consultez [Paramètres](../c-language/parameters.md). Lorsqu'une fonction en appelle une autre, la fonction appelée reçoit de la fonction appelante des valeurs pour ses paramètres. Ces valeurs sont appelées des arguments. Vous pouvez déclarer des paramètres formels à la fonction **main** pour lui permettre de recevoir des arguments de la ligne de commande. Pour cela, utilisez le format suivant :  
  
 Pour passer des informations à la fonction **main**, les paramètres sont traditionnellement nommés `argc` et `argv` bien que le compilateur C n'ait pas besoin de ces noms. Les types de `argc` et `argv` sont définis par le langage C. Traditionnellement, si un troisième paramètre est passé à **main**, ce paramètre est nommé `envp`. Les exemples figurant dans la suite de cette section expliquent comment utiliser ces trois paramètres pour accéder aux arguments de la ligne de commande. Les sections ci-dessous expliquent ces paramètres.  
  
 Consultez [Utilisation de wmain](../c-language/using-wmain.md) pour obtenir une description de la version de **main** avec les caractères larges.  
  
## <a name="see-also"></a>Voir aussi  
 [main : démarrage du programme](../cpp/main-program-startup.md)