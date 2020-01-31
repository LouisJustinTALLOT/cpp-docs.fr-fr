---
title: LoadLibrary et AfxLoadLibrary
description: Utilisation de LoadLibrary et de AfxLoadLibrary pour le chargement explicite de dll dans MSVC.
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821536"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary et AfxLoadLibrary

Les processus appellent [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) ou [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) pour une liaison explicite à une dll. (Les applications MFC utilisent [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) ou [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex).) Si la fonction est réussie, elle mappe la DLL spécifiée dans l’espace d’adressage du processus appelant et retourne un handle vers la DLL. Le descripteur est requis dans d’autres fonctions utilisées pour la liaison explicite, par exemple `GetProcAddress` et `FreeLibrary`. Pour plus d’informations, consultez [liaison explicite](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary` tente de localiser la DLL à l’aide de la même séquence de recherche que celle utilisée pour la liaison implicite. `LoadLibraryEx` vous donne davantage de contrôle sur l’ordre du chemin de recherche. Pour plus d’informations, consultez ordre de recherche de la [bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-search-order). Si le système ne peut pas trouver la DLL ou si la fonction de point d’entrée retourne FALSe, `LoadLibrary` retourne la valeur NULL. Si l’appel à `LoadLibrary` spécifie un module DLL déjà mappé dans l’espace d’adressage du processus appelant, la fonction retourne un handle de la DLL et incrémente le décompte de références du module.

Si la DLL a une fonction de point d’entrée, le système d’exploitation appelle la fonction dans le contexte du thread qui a appelé `LoadLibrary` ou `LoadLibraryEx`. La fonction de point d’entrée n’est pas appelée si la DLL est déjà attachée au processus. Cela se produit lorsqu’un appel précédent à `LoadLibrary` ou `LoadLibraryEx` pour la DLL n’a pas eu d’appel correspondant à la fonction `FreeLibrary`.

Pour les applications MFC qui chargent des dll d’extension MFC, nous vous recommandons d’utiliser `AfxLoadLibrary` ou `AfxLoadLibraryEx` au lieu de `LoadLibrary` ou `LoadLibraryEx`. Les fonctions MFC gèrent la synchronisation des threads avant de charger la DLL explicitement. Les interfaces (prototypes de fonction) à `AfxLoadLibrary` et `AfxLoadLibraryEx` sont les mêmes que `LoadLibrary` et `LoadLibraryEx`.

Si Windows ne peut pas charger la DLL, votre processus peut tenter de récupérer à partir de l’erreur. Par exemple, il peut informer l’utilisateur de l’erreur, puis demander un autre chemin d’accès à la DLL.

> [!IMPORTANT]
> Veillez à spécifier le chemin d’accès complet des dll. Le répertoire actif peut être recherché en premier lorsque des fichiers sont chargés par `LoadLibrary`. Si vous ne qualifiez pas complètement le chemin d’accès du fichier, un fichier autre que celui prévu peut être chargé. Quand vous créez une DLL, utilisez l’option de l’éditeur de liens [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) pour spécifier un ordre de recherche pour les dépendances de DLL liées statiquement. Dans vos dll, utilisez les deux chemins d’accès complets pour les dépendances explicitement chargées, et `LoadLibraryEx` ou `AfxLoadLibraryEx` appeler des paramètres pour spécifier l’ordre de recherche des modules. Pour plus d’informations, consultez sécurité de la [bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-security) et ordre de recherche de la [bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary et AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Voir aussi

- [Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
