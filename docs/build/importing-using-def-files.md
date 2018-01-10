---
title: "Importation à l’aide de fichiers DEF | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee213f1aa381415444288dbab4473cae6f5fc7b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="importing-using-def-files"></a>Importation à l'aide de fichiers DEF
Si vous choisissez d’utiliser **__declspec (dllimport)** , ainsi qu’un fichier .def, vous devez modifier le fichier .def pour utiliser des données à la place de constante afin de réduire la probabilité que le codage incorrecte entraîne un problème :  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 Le tableau suivant montre pourquoi.  
  
|Mot clé|Émet dans la bibliothèque d’importation|Exportations|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 À l’aide de **__declspec (dllimport)** et constante répertorie les deux le `imp` bibliothèque qui est créée pour permettre la liaison explicite d’importation de version et le nom non décoré dans la DLL .lib. À l’aide de **__declspec (dllimport)** et des listes de données uniquement le `imp` version du nom.  
  
 Si vous utilisez CONSTANT, les constructions de code suivantes peuvent être utilisées pour accéder à `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 - ou -  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 Toutefois, si vous utilisez des données dans votre fichier .def, seul le code compilé avec la définition suivante peut accéder à la variable `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 À l’aide de la constante est plus risquée, car si vous oubliez d’utiliser le niveau supplémentaire d’indirection, vous pourriez éventuellement accéder à la variable pointeur de la table adresses d’importation, pas la variable elle-même. Ce type de problème peut souvent se manifester par une violation d’accès, car la table d’importation adresse est actuellement en lecture seule par le compilateur et l’éditeur de liens.  
  
 L’éditeur de liens actuelle de Visual C++ émet un avertissement s’il voit constante dans le fichier .def pour prendre en compte pour ce cas. La seule raison d’utiliser constante est si vous ne pouvez pas recompiler un fichier objet quelconque dans lequel le fichier d’en-tête ne pas répertorier **__declspec (dllimport)** sur le prototype.  
  
## <a name="see-also"></a>Voir aussi  
 [Importation dans une application](../build/importing-into-an-application.md)
