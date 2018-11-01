---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 241f31717274c73a658f4cddf4e6e1ef4e40b402
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457666"
---
# <a name="getprocaddress"></a>GetProcAddress

Les processus liés de manière explicite à une DLL appellent [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) pour obtenir l’adresse d’une fonction exportée dans la DLL. Vous utilisez le pointeur de fonction retourné pour appeler la fonction de la DLL. **GetProcAddress** prend comme paramètres le handle de module DLL (retourné par **LoadLibrary**, `AfxLoadLibrary`, ou **GetModuleHandle**) et soit le nom de la fonction que vous souhaitez à l’appel ou l’ordinal d’exportation de la fonction.

Étant donné que vous appelez la fonction DLL via un pointeur et qu’aucune vérification de type lors de la compilation, assurez-vous que les paramètres de la fonction sont corrects, afin que vous ne pas enfreindre la mémoire allouée sur la pile et provoquer une violation d’accès. Une méthodes permettant de fournir une sécurité de type consiste à examiner les prototypes des fonctions exportées et créer des typedefs correspondants pour les pointeurs de fonction. Exemple :

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

Manière dont vous spécifiez la fonction qui vous intéresse lorsque vous appelez **GetProcAddress** dépend de la façon dont la DLL a été générée.

Vous ne pouvez obtenir l’ordinal d’exportation si la DLL que vous établissez la liaison est générée avec un fichier de définition (.def) de module et si les ordinaux sont listés avec les fonctions dans le **exportations** section du fichier .def de la DLL. Appel **GetProcAddress** avec une exportation ordinal, plutôt que le nom de fonction, est légèrement plus rapide si la DLL possède de nombreuses fonctions exportées car les ordinaux d’exportation servent de la table d’exportation de l’index dans la DLL. Avec un ordinal d’exportation, **GetProcAddress** peut localiser la fonction directement au lieu de comparer le nom spécifié aux noms des fonctions dans la table d’exportation de la DLL. Toutefois, vous devez appeler **GetProcAddress** avec un ordinal d’exportation uniquement si vous contrôlez l’assignation des ordinaux aux fonctions exportées dans le fichier .def.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Comment lier de manière implicite à une DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [LoadLibrary et AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Exportation à partir d’une DLL à l’aide de fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)