---
title: Déchargement d'une DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 284a9cb9268c8c794379c6a5468b0f2b9092b7d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317456"
---
# <a name="unloading-a-delay-loaded-dll"></a>Déchargement d'une DLL à chargement différé

L’application d’assistance de chargement différé fournie par défaut vérifie si les descripteurs de chargement différé ont un pointeur et une copie de la table d’origine d’adresse d’importation (IAT) dans le champ pUnloadIAT. Si c’est le cas, il enregistre un pointeur dans une liste pour le descripteur de délai d’importation. Cela permet à la fonction d’assistance trouver la DLL par nom pour prendre en charge le déchargement explicite de cette DLL.

Voici les structures et fonctions associées pour le déchargement explicite d’une DLL à chargement différé :

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

La structure UnloadInfo est implémentée à l’aide d’une classe C++ qui utilise **LocalAlloc** et **LocalFree** mises en œuvre en tant que son opérateur **nouveau** et opérateur  **supprimer** respectivement. Ces options sont conservées dans une liste liée standard avec __puiHead comme le début de la liste.

Appel __FUnloadDelayLoadedDLL va tenter de trouver le nom que vous fournissez dans la liste des DLL chargées (une correspondance exacte est requise). Si la trouvé, la copie de la table IAT dans pUnloadIAT est copiée sur le haut de la table IAT en cours d’exécution pour restaurer les pointeurs de thunk, la bibliothèque est libérée avec **FreeLibrary**, la mise en correspondance **UnloadInfo** enregistrement est dissocié de la liste et supprimés et la valeur TRUE est retournée.

L’argument de la fonction __FUnloadDelayLoadedDLL2 respecte la casse. Par exemple, vous devez spécifier :

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

et non :

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Voir aussi

[Présentation de la fonction d’assistance](understanding-the-helper-function.md)
