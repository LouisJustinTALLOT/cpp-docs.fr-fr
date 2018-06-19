---
title: Fichiers de commandes CL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 367ea6dc22777b473cad44f35b1f5e4c34528471
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369875"
---
# <a name="cl-command-files"></a>Fichiers de commandes CL
Un fichier de commandes est un fichier texte qui contient les options et les noms de fichiers vous indiquez dans le cas contraire le [ligne de commande](../../build/reference/compiler-command-line-syntax.md) ou spécifier à l’aide de la [variable d’environnement CL](../../build/reference/cl-environment-variables.md). CL accepte un fichier de commandes du compilateur en tant qu’argument dans la variable d’environnement CL ou sur la ligne de commande. Contrairement à la ligne de commande ou à la variable d'environnement CL, un fichier de commandes vous permet d'utiliser plusieurs lignes d'options et de noms de fichiers.  
  
 Options et les noms de fichiers dans un fichier de commandes sont traités en fonction de l’emplacement d’un nom de fichier de commande dans la variable d’environnement CL ou sur la ligne de commande. Cependant, si l’option /link apparaît dans le fichier de commandes, toutes les options sur le reste de la ligne sont passées à l’éditeur de liens. Options dans les lignes suivantes du fichier de commandes et les options sur la ligne de commande après l’appel de fichier de commandes sont toujours acceptées en tant qu’options du compilateur. Pour plus d’informations sur la façon dont l’ordre des options influe sur leur interprétation, consultez [ordre des Options CL](../../build/reference/order-of-cl-options.md).  
  
 Un fichier de commandes ne doit pas contenir la commande CL. Chaque option doit commencer et se terminer sur la même ligne ; Vous ne pouvez pas utiliser la barre oblique inverse (\\) pour combiner une option répartie sur deux lignes.  
  
 Un fichier de commandes est spécifié par un arobase (@) suivi d’un nom de fichier ; le nom de fichier peut spécifier un chemin d’accès absolu ou relatif.  
  
 Par exemple, si la commande suivante est dans un fichier de réponse :  
  
```  
/Og /link LIBC.LIB  
```  
  
 et que vous spécifiez la commande CL suivante :  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 la commande CL est comme suit :  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 Notez que la ligne de commande et le fichier de commandes est combinées efficacement.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)