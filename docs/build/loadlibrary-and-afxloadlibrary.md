---
title: LoadLibrary et AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493210"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary et AfxLoadLibrary

Les processus appellent [LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) ou [LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (ou [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) pour établir une liaison explicite à une dll. Si la fonction est réussie, elle mappe la DLL spécifiée dans l’espace d’adressage du processus appelant et retourne un handle vers la dll qui peut être utilisée avec d’autres fonctions dans une liaison explicite, par `GetProcAddress` exemple `FreeLibrary`et.

`LoadLibrary`tente de localiser la DLL à l’aide de la même séquence de recherche que celle utilisée pour la liaison implicite. Si le système ne trouve pas la dll ou si la fonction de point d’entrée retourne `LoadLibrary` false, retourne la valeur null. Si l’appel à `LoadLibrary` spécifie un module dll qui est déjà mappé dans l’espace d’adressage du processus appelant, la fonction retourne un handle de la dll et incrémente le décompte de références du module.

Si la DLL a une fonction de point d’entrée, le système d’exploitation appelle la fonction dans le contexte du thread qui `LoadLibrary`a appelé. La fonction de point d’entrée n’est pas appelée si la dll est déjà attachée au processus en raison d’un `LoadLibrary` appel précédent à qui n’a pas `FreeLibrary` d’appel correspondant à la fonction.

Pour les applications MFC qui chargent des dll d’extension MFC, nous `AfxLoadLibrary` vous recommandons `LoadLibrary`d’utiliser au lieu de. `AfxLoadLibrary`gère la synchronisation des threads `LoadLibrary`avant d’appeler. L’interface (prototype de fonction) `AfxLoadLibrary` est `LoadLibrary`identique à.

Si Windows ne peut pas charger la DLL, le processus peut tenter de récupérer à partir de l’erreur. Par exemple, le processus peut informer l’utilisateur de l’erreur et demander à l’utilisateur de spécifier un autre chemin d’accès à la DLL.

> [!IMPORTANT]
> Veillez à spécifier le chemin d’accès complet des dll. Le répertoire actif est recherché en premier lors du chargement des fichiers. Si vous ne qualifiez pas le chemin d’accès du fichier, un fichier qui n’est pas celui prévu peut être chargé. Pour éviter cela, vous pouvez également utiliser l’option de l’éditeur de liens [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) .

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary et AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Voir aussi

- [Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
