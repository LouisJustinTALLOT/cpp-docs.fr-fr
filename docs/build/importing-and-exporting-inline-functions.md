---
title: Importation et exportation de fonctions Inline | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b666d450766a5a285f02517d92d5eb4dc3f29c68
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368575"
---
# <a name="importing-and-exporting-inline-functions"></a>Importation et exportation de fonctions inline
Les fonctions importées peuvent être définies comme inline. L’effet est à peu près identique à la définition d’une fonction inline standard ; les appels à la fonction sont développés en code inline, à l’instar d’une macro. Il s’agit essentiellement utile comme un moyen de prendre en charge C++ classes utilisées dans une DLL qui peuvent être inline à certaines de leurs membres fonctions par souci d’efficacité.  
  
 Une fonctionnalité d’une fonction inline importée est que vous pouvez prendre son adresse en C++. Le compilateur retourne l’adresse de la copie de la fonction inline résidant dans la DLL. Une autre fonctionnalité des fonctions inline importées est que vous pouvez initialiser les données locales statiques de la fonction importée, contrairement aux données importées globales.  
  
> [!CAUTION]
>  Soyez prudent lorsque vous fournissant des fonctions inline importées, car elles peuvent donner lieu à des conflits de versions. Une fonction inline est développée en code d’application ; Par conséquent, si vous réécrivez ultérieurement la fonction, il ne pas mis à jour, sauf si l’application elle-même est recompilée. (Normalement, DLL (fonctions) peuvent être mis à jour sans régénération des applications qui les utilisent.)  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL](../build/exporting-from-a-dll.md)  
  
-   [Exporter à partir d’une DLL à l’aide. Fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Importation et exportation](../build/importing-and-exporting.md)