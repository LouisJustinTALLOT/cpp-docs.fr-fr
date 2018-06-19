---
title: Déchargement explicite d’une DLL à chargement différé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 171acf9689c01649b86c2383d17136c926e25c57
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374172"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Déchargement explicite d'une DLL à chargement différé
Le [/Delay](../../build/reference/delay-delay-load-import-settings.md): option de l’éditeur de liens unload vous permet de décharger une DLL à chargement différé. Par défaut, lorsque votre code décharge la DLL (à l’aide / Delay : Unload et **__FUnloadDelayLoadedDLL2**), les importations à chargement différé restent dans la table d’adresses d’importation (IAT). Toutefois, si vous utilisez/DELAY : Unload sur la ligne de commande de l’éditeur de liens, la fonction d’assistance prendra en charge le déchargement explicite de la DLL de la réinitialisation de la table IAT sous sa forme d’origine ; les pointeurs désormais non valides sont écrasées. La table IAT est un champ dans le [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) qui contient l’adresse d’une copie de l’IAT d’origine (s’il existe).  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD  
#include <windows.h>  
#include <delayimp.h>  
#include "MyDll.h"  
#include <stdio.h>  
  
#pragma comment(lib, "delayimp")  
#pragma comment(lib, "MyDll")  
int main()  
{  
    BOOL TestReturn;  
    // MyDLL.DLL will load at this point  
    fnMyDll();  
  
    //MyDLL.dll will unload at this point  
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");  
  
    if (TestReturn)  
        printf_s("\nDLL was unloaded");  
    else  
        printf_s("\nDLL was not unloaded");  
}  
```  
  
### <a name="comments"></a>Commentaires  
 Remarques importantes sur le déchargement d’une DLL à chargement différé :  
  
-   Vous pouvez trouver l’implémentation de la **__FUnloadDelayLoadedDLL2** fonction dans le fichier \VC7\INCLUDE\DELAYHLP. CPP.  
  
-   Le paramètre name de la **__FUnloadDelayLoadedDLL2** (fonction) doit exactement correspondre (y compris les cas) que la bibliothèque d’importation (cette chaîne se trouve également dans la table d’importation de l’image). Vous pouvez afficher le contenu de la bibliothèque d’importation avec [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Si une correspondance de chaîne de la casse est souhaitée, vous pouvez mettre à jour **__FUnloadDelayLoadedDLL2** utiliser une des fonctions de chaîne CRT ou un appel API Windows.  
  
 Consultez [déchargement d’une DLL à chargement différé](../../build/reference/unloading-a-delay-loaded-dll.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)