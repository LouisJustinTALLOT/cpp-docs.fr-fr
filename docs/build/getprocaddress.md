---
description: 'En savoir plus sur : GetProcAddress'
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 32f0d6d623ea3a4499603a1b76e2c320537820fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162870"
---
# <a name="getprocaddress"></a>GetProcAddress

Les processus de liaison explicite à une DLL appellent [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction exportée dans la dll. Vous utilisez le pointeur de fonction retourné pour appeler la fonction DLL. **GetProcAddress** prend comme paramètres le handle du module dll (retourné par **LoadLibrary**, `AfxLoadLibrary` ou **GetModuleHandle**) et prend soit le nom de la fonction que vous souhaitez appeler, soit l’ordinal d’exportation de la fonction.

Étant donné que vous appelez la fonction DLL par le biais d’un pointeur et qu’il n’y a aucune vérification de type au moment de la compilation, assurez-vous que les paramètres de la fonction sont corrects afin de ne pas surExécuter la mémoire allouée sur la pile et de provoquer une violation d’accès. L’une des façons d’assurer la sécurité des types consiste à examiner les prototypes de fonction des fonctions exportées et à créer des typedefs correspondants pour les pointeurs de fonction. Par exemple :

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

La façon dont vous spécifiez la fonction que vous souhaitez lorsque vous appelez **GetProcAddress** dépend de la façon dont la dll a été générée.

Vous pouvez obtenir l’ordinal d’exportation uniquement si la DLL à laquelle vous effectuez la liaison est créée à l’aide d’un fichier de définition de module (. def) et si les ordinaux sont répertoriés avec les fonctions de la section **exports** du fichier. def de la dll. L’appel de **GetProcAddress** avec un ordinal d’exportation, par opposition au nom de la fonction, est légèrement plus rapide si la dll a de nombreuses fonctions exportées, car les ordinaux d’exportation servent d’index dans la table d’exportation de la dll. Avec un ordinal d’exportation, **GetProcAddress** peut localiser la fonction directement au lieu de comparer le nom spécifié aux noms de fonctions dans la table d’exportation de la dll. Toutefois, vous devez appeler **GetProcAddress** avec un ordinal d’exportation uniquement si vous avez le contrôle sur l’assignation des ordinaux aux fonctions exportées dans le fichier. def.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportation à partir d’une DLL à l’aide de fichiers DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
