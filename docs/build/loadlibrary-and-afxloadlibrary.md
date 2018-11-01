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
ms.openlocfilehash: 7c0b63d80a8b4b03b55d6e50af6c08a8de0937de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596544"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary et AfxLoadLibrary

Traite l’appel [LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) ou [LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(ou [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) pour une liaison explicite à une DLL. Si la fonction réussit, il mappe la DLL spécifiée dans l’espace d’adressage du processus appelant et retourne un handle vers la DLL qui peut être utilisée avec d’autres fonctions pour une liaison explicite, par exemple, `GetProcAddress` et `FreeLibrary`.

`LoadLibrary` tente de localiser la DLL à l’aide de la séquence de recherche qui est utilisée pour la liaison implicite. Si le système ne trouve pas la DLL ou si la fonction de point d’entrée retourne FALSE, `LoadLibrary` renvoie la valeur NULL. Si l’appel à `LoadLibrary` spécifie un module DLL qui est déjà mappé dans l’espace d’adressage du processus appelant, la fonction retourne un handle de la DLL et incrémente le décompte de références du module.

Si la DLL possède une fonction de point d’entrée, le système d’exploitation appelle la fonction dans le contexte du thread qui a appelé `LoadLibrary`. La fonction de point d’entrée n’est pas appelée si la DLL est déjà attachée au processus en raison d’un appel précédent à `LoadLibrary` qui a sans appel correspondant à la `FreeLibrary` (fonction).

Pour les applications MFC qui chargent des DLL d’extension MFC, nous vous recommandons d’utiliser `AfxLoadLibrary` au lieu de `LoadLibrary`. `AfxLoadLibrary` gère la synchronisation des threads avant d’appeler `LoadLibrary`. L’interface (prototype de fonction) à `AfxLoadLibrary` est identique à `LoadLibrary`.

Si Windows ne peut pas charger la DLL, le processus peut tenter de récupérer à partir de l’erreur. Par exemple, le processus peut notifier l’utilisateur de l’erreur et demandez à l’utilisateur de spécifier un autre chemin d’accès à la DLL.

> [!IMPORTANT]
> Veillez à spécifier le chemin d’accès complet de toute DLL. Le répertoire actif est tout d’abord recherché lors du chargement de fichiers. Si vous ne sont pas éligibles le chemin d’accès du fichier, un fichier qui n’est pas celle prévue peut être chargé. Une autre façon d’éviter ce problème consiste à l’aide de la [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) option de l’éditeur de liens.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Comment lier de manière implicite à une DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Dynamic-Link Library Search Order](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary et AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Voir aussi

- [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)
