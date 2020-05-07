---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552240"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep`enregistre les informations du compteur de profil actuel dans un fichier, puis réinitialise les compteurs. Utilisez la fonction lors de la formation de l’optimisation guidée par profil pour écrire toutes les données de profil `.pgc` du programme en cours d’exécution dans un fichier en vue d’une utilisation ultérieure dans la build d’optimisation.

## <a name="syntax"></a>Syntaxe

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Chaîne d’identification du fichier enregistré `.pgc` .

## <a name="remarks"></a>Notes 

Vous pouvez appeler `PgoAutoSweep` à partir de votre application pour enregistrer et réinitialiser les données de profil à tout moment pendant l’exécution de l’application. Dans une build instrumentée, `PgoAutoSweep` capture les données de profilage actuelles, les enregistre dans un fichier et réinitialise les compteurs de profil. C’est l’équivalent de l’appel de la commande [pgosweep](pgosweep.md) à un point spécifique dans votre fichier exécutable. Dans une version optimisée `PgoAutoSweep` , n’est pas une opération.

Les données de compteur de profil enregistrées sont placées dans un fichier nommé *base_name*-*Name*! *value*. PGC, où *base_name* est le nom de base de l’exécutable, *Name* est le paramètre passé à `PgoAutoSweep`, et *value* est une valeur unique, généralement un nombre à croissance monotone, pour éviter les collisions de nom de fichier.

Les `.pgc` fichiers créés par `PgoAutoSweep` doivent être fusionnés dans un `.pgd` fichier à utiliser pour créer un exécutable optimisé. Vous pouvez utiliser la commande [pgomgr](pgomgr.md) pour effectuer la fusion.

Vous `.pgd` pouvez passer le nom du fichier fusionné à l’éditeur de liens pendant la génération de l’optimisation à l’aide de l’argument **PGD =**_filename_ de l’option de l’éditeur de liens [/USEPROFILE](reference/useprofile.md) , ou à l’aide de l’option de l’éditeur de liens **/PGD** déconseillée. Si vous fusionnez `.pgc` les fichiers dans un fichier nommé *base_name*. pgd, vous n’avez pas besoin de spécifier le nom de fichier sur la ligne de commande, car l’éditeur de liens sélectionne ce nom de fichier par défaut.

La `PgoAutoSweep` fonction conserve le paramètre de sécurité des threads spécifié lors de la création de la build instrumentée. Si vous utilisez le paramètre par défaut ou si vous spécifiez l’argument **noexact** pour l’option de l’éditeur de `PgoAutoSweep` liens [/GENPROFILE ou/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , les appels à ne sont pas thread-safe. L’argument **exact** crée un exécutable instrumenté thread-safe et plus précis, mais plus lent.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun. h>|

L’exécutable doit inclure le fichier pgobootrun. lib dans les bibliothèques liées. Ce fichier est inclus dans votre installation de Visual Studio, dans le répertoire des bibliothèques VC pour chaque architecture prise en charge.

## <a name="example"></a> Exemple

L’exemple ci- `PgoAutoSweep` dessous utilise pour `.pgc` créer deux fichiers à des moments différents au cours de l’exécution. Le premier contient des données qui décrivent le comportement `count` d’exécution jusqu’à ce que soit égal à 3, et le second contient les données collectées après ce point jusqu’à l’arrêt de l’application juste avant.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

Dans une invite de commandes développeur, compilez le code dans un fichier objet à l’aide de cette commande :

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Générez ensuite une build instrumentée pour l’apprentissage à l’aide de cette commande :

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Exécutez l’exécutable instrumenté pour capturer les données d’apprentissage. Les données générées par les appels `PgoAutoSweep` à sont enregistrées dans des fichiers nommés PgoAutoSweep-func1 ! 1. pgc et PgoAutoSweep-Func2 ! 1. PGC. La sortie du programme doit ressembler à ceci, car il s’exécute :

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

Fusionnez les données enregistrées dans une base de données de formation des profils en exécutant la commande **pgomgr** :

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

La sortie de cette commande ressemble à ceci :

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Vous pouvez désormais utiliser ces données d’apprentissage pour générer une build optimisée. Utilisez cette commande pour générer le fichier exécutable optimisé :

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
