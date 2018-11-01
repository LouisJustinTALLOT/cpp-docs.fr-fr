---
title: Déchargement explicite d'une DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: a433c9987d665aeeb910edbadac692ba9c286e3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605385"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Déchargement explicite d'une DLL à chargement différé

Le [/retarder](../../build/reference/delay-delay-load-import-settings.md): option de l’éditeur de liens unload vous permet de décharger une DLL à chargement différé. Par défaut, lorsque votre code décharge la DLL (à l’aide / Delay : Unload et **__FUnloadDelayLoadedDLL2**), les importations à chargement différé restent dans la table d’adresses d’importation (IAT). Toutefois, si vous utilisez/DELAY : Unload sur la ligne de commande de l’éditeur de liens, la fonction d’assistance prendra en charge le déchargement explicite de la DLL, la réinitialisation de la table IAT dans sa forme d’origine ; les pointeurs désormais non valides seront remplacées. L’IAT est un champ dans le [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) qui contient l’adresse d’une copie de la table IAT d’origine (si elle existe).

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

- Vous trouverez l’implémentation de la **__FUnloadDelayLoadedDLL2** fonction dans le fichier \VC7\INCLUDE\DELAYHLP. CPP.

- Le paramètre name de la **__FUnloadDelayLoadedDLL2** fonction doit correspondre exactement (y compris les cas) ce que la bibliothèque d’importation contient (cette chaîne se trouve également dans la table d’importation dans l’image). Vous pouvez afficher le contenu de la bibliothèque d’importation avec [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Si une correspondance de chaîne de non-respect de la casse est souhaitée, vous pouvez mettre à jour **__FUnloadDelayLoadedDLL2** à utiliser une des fonctions de chaîne CRT ou un appel d’API de Windows.

Consultez [déchargement d’une DLL à chargement différé](../../build/reference/unloading-a-delay-loaded-dll.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)