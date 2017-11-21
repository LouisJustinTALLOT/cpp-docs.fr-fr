---
title: "Importation dans une Application à l’aide de __declspec (dllimport) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f16c9f5c96712c311928e0389fec0a1ce1f0dca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Importation dans une application à l'aide de __declspec(dllimport)
Un programme qui utilise des symboles publics définis par une DLL est réputé les importer. Lorsque vous créez des fichiers d’en-tête pour les applications qui utilisent vos DLL pour la génération, utilisez **__declspec (dllimport)** sur les déclarations des symboles publics. Le mot clé **__declspec (dllimport)** fonctionne si vous exportez des fichiers .def ou avec le **__declspec (dllexport)** (mot clé).  
  
 Pour rendre votre code plus lisible, définissez une macro pour **__declspec (dllimport)** , puis utilisez la macro pour déclarer chaque symbole importé :  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 À l’aide de **__declspec (dllimport)** est facultative dans les déclarations de fonction, mais le compilateur produit un code plus efficace si vous utilisez ce mot clé. Toutefois, vous devez utiliser **__declspec (dllimport)** à l’exécutable importateur accéder aux objets et les symboles de données publics de la DLL. Notez que les utilisateurs de votre DLL doivent toujours être liée à une bibliothèque d’importation.  
  
 Vous pouvez utiliser le même fichier d’en-tête pour la DLL et l’application cliente. Pour ce faire, utilisez un symbole de préprocesseur spécial qui indique si vous générez la DLL ou l’application cliente. Exemple :  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importations mutuelles](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Importation dans une application](../build/importing-into-an-application.md)