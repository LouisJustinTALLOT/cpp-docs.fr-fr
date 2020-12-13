---
description: 'En savoir plus sur : déchargement d’une DLL Delay-Loaded'
title: Déchargement d'une DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: fd733bfa02a6d90eecb1b617288d368d33766282
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178938"
---
# <a name="unloading-a-delay-loaded-dll"></a>Déchargement d'une DLL à chargement différé

Le programme d’assistance de chargement différé fourni par défaut vérifie si les descripteurs de chargement différé ont un pointeur et une copie de la table d’adresses d’importation (IAT) d’origine dans le champ pUnloadIAT. Si c’est le cas, il enregistre un pointeur dans une liste dans le descripteur de délai d’importation. Cela permet à la fonction d’assistance de rechercher la DLL par nom afin de prendre en charge le déchargement explicite de cette DLL.

Voici les structures et les fonctions associées pour décharger explicitement une DLL à chargement différé :

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

La structure UnloadInfo est implémentée à l’aide d’une classe C++ qui utilise les implémentations de **LocalAlloc** et **LocalFree** respectivement comme opérateur **`new`** et opérateur **`delete`** . Ces options sont conservées dans une liste liée standard à l’aide de __puiHead comme en-tête de la liste.

L’appel de __FUnloadDelayLoadedDLL tente de trouver le nom que vous fournissez dans la liste des DLL chargées (une correspondance exacte est requise). Si elle est trouvée, la copie de l’IAT dans pUnloadIAT est copiée sur le haut de la IAT en cours d’exécution pour restaurer les pointeurs de thunk, la bibliothèque est libérée avec **FreeLibrary**, l’enregistrement **UnloadInfo** correspondant est dissocié de la liste et supprimé, et la valeur true est retournée.

L’argument de la fonction __FUnloadDelayLoadedDLL2 respecte la casse. Par exemple, vous devez spécifier :

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

et non :

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Voir aussi

[Fonctionnement de la fonction d’assistance](understanding-the-helper-function.md)
