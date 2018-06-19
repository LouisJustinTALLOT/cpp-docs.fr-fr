---
title: -BASE (adresse de Base) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4090a3e8d2f9f3bdcb68875d94a1b84e7bff0f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376622"
---
# <a name="base-base-address"></a>/BASE (Adresse de base)
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 L’option de BASE définit une adresse de base pour le programme, en remplacement de l’emplacement par défaut pour un .exe ou un fichier DLL. L’adresse de base par défaut pour un fichier .exe est 0 x 400000 pour les images 32 bits ou 0x140000000 pour les images de 64 bits. Pour une DLL, l’adresse de base par défaut est 0 x 10000000 pour les images 32 bits ou 0x180000000 pour les images de 64 bits. Sur les systèmes d’exploitation qui ne prennent pas en charge la randomisation du format d’espace d’adresse (ASLR), ou lorsque l’option : no a été définie, le système d’exploitation tente tout d’abord charger un programme à son spécifié ou l’adresse de base par défaut. Si un espace suffisant y ne figure pas disponible, le système réaffecte le programme. Pour éviter le réadressage, utilisez le [/fixe](../../build/reference/fixed-fixed-base-address.md) option.  
  
 L’éditeur de liens génère une erreur si *adresse* n’est pas un multiple de 64 Ko. Vous pouvez éventuellement spécifier la taille du programme ; l’éditeur de liens émet un avertissement si le programme ne tiennent pas dans la taille spécifiée.  
  
 Sur la ligne de commande, une autre façon de spécifier l’adresse de base est à l’aide d’un fichier de réponse d’adresse de base. Un fichier de réponse d’adresse de base est un fichier texte qui contient les adresses de base et les tailles facultatif de toutes les DLL que votre programme utilise et une clé de texte unique pour chaque adresse de base. Pour spécifier une adresse de base à l’aide d’un fichier de réponse, utilisez un arobase (@) suivi du nom du fichier de réponse, *nom de fichier*, suivi par une virgule, puis le `key` valeur pour l’adresse de base à utiliser dans le fichier. L’éditeur de liens recherche *nom de fichier* dans le chemin spécifié, ou si aucun chemin d’accès n’est spécifié, dans les répertoires spécifiés dans la variable d’environnement LIB. Chaque ligne dans *nom de fichier* représente une DLL et présente la syntaxe suivante :  
  
```  
  
key address [size] ;comment  
```  
  
 Le `key` est une chaîne de caractères alphanumériques et n’est pas respecter la casse. Il s’agit généralement du nom d’une DLL, mais ne sont pas nécessairement. Le `key` est suivie d’une base de *adresse* dans la notation en langage C, hexadécimale ou décimale et une valeur maximale facultatif `size`. Les trois arguments sont séparés par des espaces ou des tabulations. L’éditeur de liens émet un avertissement en cas spécifié `size` est inférieur à l’espace d’adressage virtuel requis par le programme. A `comment` est spécifié par un point-virgule ( ;) et peuvent se trouver sur la même ou à une ligne distincte. L’éditeur de liens ignore tout le texte compris entre le point-virgule à la fin de la ligne. Cet exemple montre une partie d’un tel fichier :  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 Si le fichier qui contient ces lignes s’appelle DLLS.txt, la commande suivante s’applique à ces informations :  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>Notes  
 Pour des raisons de sécurité, Microsoft recommande d’utiliser le [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) option au lieu de spécifier les adresses de base pour les fichiers exécutables. Cela génère une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement à l’aide de la fonctionnalité espace d’adresse (ASLR) de randomisation de Windows. L’option /DYNAMICBASE est activé par défaut.  
  
 Une autre consiste à définir l’adresse de base à l’aide de la *BASE* argument dans un [nom](../../build/reference/name-c-cpp.md) ou [bibliothèque](../../build/reference/library.md) instruction. Le /BASE et [/DLL](../../build/reference/dll-build-a-dll.md) options réunies sont équivalentes à la **bibliothèque** instruction.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Développez le **l’éditeur de liens** dossier.  
  
3.  Choisissez le **avancé** page de propriétés.  
  
4.  Modifier la **adresse de Base** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)