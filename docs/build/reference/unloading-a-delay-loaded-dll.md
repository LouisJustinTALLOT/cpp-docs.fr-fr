---
title: Déchargement d’une DLL à chargement différé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724ee2ac3987c855f5e2102dee35d12785726641
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375212"
---
# <a name="unloading-a-delay-loaded-dll"></a>Déchargement d'une DLL à chargement différé
L’application d’assistance de chargement différé fournie par défaut vérifie si les descripteurs de chargement différé ont un pointeur et une copie de la table des adresses importation (IAT) d’origine dans le champ pUnloadIAT. Dans ce cas, il enregistre un pointeur dans une liste pour le descripteur de délai d’importation. Cela permet à la fonction d’assistance de trouver la DLL par un nom pour prendre en charge le déchargement explicite de cette DLL.  
  
 Voici les structures et fonctions associées pour le déchargement explicite d’une DLL à chargement différé :  
  
```  
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
  
 Appel __FUnloadDelayLoadedDLL va tenter de trouver le nom vous fournissez dans la liste des DLL chargées (une correspondance exacte est nécessaire). Si la trouvé, la copie de la table IAT dans pUnloadIAT est copiée sur la partie supérieure de la table IAT en cours d’exécution pour restaurer les pointeurs de thunk, la bibliothèque est libérée avec **FreeLibrary**, la mise en correspondance **UnloadInfo** enregistrement est dissocié de la liste et supprimées et TRUE est.  
  
 L’argument de la fonction __FUnloadDelayLoadedDLL2 respecte la casse. Par exemple, vous devez spécifier :  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 et non :  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la fonction d’assistance](understanding-the-helper-function.md)