---
title: GetProcAddress | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cec73a7d7aa212c6f53bc2654db6fe40ff96472a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367964"
---
# <a name="getprocaddress"></a>GetProcAddress
Les processus liés de manière explicite à un appel DLL [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) pour obtenir l’adresse d’une fonction exportée dans la DLL. Vous utilisez le pointeur de fonction retourné pour appeler la fonction de la DLL. **GetProcAddress** prend comme paramètres de la poignée du module DLL (retourné par **LoadLibrary**, `AfxLoadLibrary`, ou **GetModuleHandle**) et prend le nom de la fonction que vous souhaitez à l’appel ou l’ordinal d’exportation de la fonction.  
  
 Étant donné que vous appelez la fonction DLL via un pointeur et il n’existe aucune vérification de type lors de la compilation, assurez-vous que les paramètres de la fonction sont corrects, afin que vous ne pas dépasser la mémoire allouée sur la pile et provoquer une violation d’accès. Une façon d’assurer la sécurité de type consiste à examiner les prototypes des fonctions exportées et de créer des typedefs correspondants pour les pointeurs de fonction. Par exemple :  
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 Manière dont vous spécifiez la fonction qui vous intéresse lorsque vous appelez **GetProcAddress** dépend de la génération de la DLL.  
  
 Vous ne pouvez obtenir l’ordinal d’exportation si la DLL que vous établissez la liaison est générée avec un fichier de définition (.def) de module et si les ordinaux sont listés avec les fonctions dans le **exportations** section du fichier .def de la DLL. Appel de **GetProcAddress** avec une exportation ordinal, plutôt que le nom de fonction, est légèrement plus rapide si la DLL possède de nombreuses fonctions exportées car les ordinaux d’exportation servent de la table d’exportation de l’index dans la DLL. Avec un ordinal d’exportation, **GetProcAddress** peut localiser la fonction directement au lieu de comparer le nom spécifié pour les noms de fonctions dans la table d’exportation de la DLL. Toutefois, vous devez appeler **GetProcAddress** avec un ordinal d’exportation uniquement si vous avez un contrôle sur l’assignation des ordinaux aux fonctions exportées dans le fichier .def.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Comment lier de manière implicite à une DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [LoadLibrary et AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Exportation à partir d’une DLL à l’aide de fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)