---
description: 'En savoir plus sur : déchargement explicite d’une DLL Delay-Loaded'
title: Déchargement explicite d'une DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: 03df08487acc1be05226021d6b7c1593eb0f031b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192380"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Déchargement explicite d'une DLL à chargement différé

L’option [/delay](delay-delay-load-import-settings.md): Unload de l’éditeur de liens vous permet de décharger une dll qui a été chargée en différé. Par défaut, lorsque votre code décharge la DLL (à l’aide de/delay : unload et **__FUnloadDelayLoadedDLL2**), les importations à chargement différé sont conservées dans la table d’adresses d’importation (IAT). Toutefois, si vous utilisez/Delay : Unload sur la ligne de commande de l’éditeur de liens, la fonction d’assistance prend en charge le déchargement explicite de la DLL, réinitialisant la valeur IAT à sa forme d’origine ; désormais, les pointeurs non valides seront remplacés. L’IAT est un champ dans le [ImgDelayDescr](calling-conventions-parameters-and-return-type.md) qui contient l’adresse d’une copie de l’IAT d’origine (le cas échéant).

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

- Vous pouvez trouver l’implémentation de la fonction **__FUnloadDelayLoadedDLL2** dans le fichier \VC7\INCLUDE\DELAYHLP. Cotisations.

- Le paramètre Name de la fonction **__FUnloadDelayLoadedDLL2** doit correspondre exactement (y compris la casse) à la bibliothèque d’importation (cette chaîne se trouve également dans la table import de l’image). Vous pouvez afficher le contenu de la bibliothèque d’importation avec [DUMPBIN/DEPENDENTS](dependents.md). Si une correspondance de chaîne ne respectant pas la casse est souhaitée, vous pouvez mettre à jour **__FUnloadDelayLoadedDLL2** pour utiliser l’une des fonctions de chaîne CRT ou un appel d’API Windows.

Pour plus d’informations, consultez [déchargement d’une dll de Delay-Loaded](unloading-a-delay-loaded-dll.md) .

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
