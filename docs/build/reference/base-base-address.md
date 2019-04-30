---
title: /BASE (Adresse de base)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
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
ms.openlocfilehash: dc6380903af0be2e6696ca3589813c249f71dd05
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341024"
---
# <a name="base-base-address"></a>/BASE (Adresse de base)

Spécifie l’adresse de base pour un programme.

## <a name="syntax"></a>Syntaxe

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>Notes

> [!NOTE]
> Pour des raisons de sécurité, Microsoft recommande d’utiliser le [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) option au lieu de spécifier les adresses de base pour vos fichiers exécutables. Cela génère une image exécutable pouvant être aléatoirement redéfinie au moment du chargement à l’aide de la fonctionnalité espace d’adresse disposition randomization (ASLR) de Windows. L’option /DYNAMICBASE est activé par défaut.

Le/option de BASE définit une adresse de base pour le programme, en remplaçant l’emplacement par défaut pour un .exe ou d’un fichier DLL. L’adresse de base par défaut pour un fichier .exe est 0 x 400000 pour les images 32 bits ou 0x140000000 pour les images de 64 bits. Pour une DLL, l’adresse de base par défaut est 0 x 10000000 pour les images 32 bits ou 0x180000000 pour les images de 64 bits. Sur les systèmes d’exploitation qui ne prennent pas en charge la randomisation du format d’espace d’adresse (ASLR), ou lorsque l’option/DYNAMICBASE : no a été définie, le système d’exploitation tente tout d’abord charger un programme pour le son spécifié ou l’adresse de base par défaut. Absence suffisamment d’espace disponible, le système réaffecte le programme. Pour éviter le réadressage, utilisez le [/FIXED](fixed-fixed-base-address.md) option.

L’éditeur de liens génère une erreur si *adresse* n’est pas un multiple de 64 Ko. Vous pouvez éventuellement spécifier la taille du programme ; l’éditeur de liens émet un avertissement si le programme ne peut pas tenir dans la taille spécifiée.

Sur la ligne de commande, un autre pour spécifier l’adresse de base consiste à l’aide d’un fichier de réponse d’adresse de base. Un fichier de réponse d’adresse de base est un fichier texte qui contient les adresses de base et les tailles facultatifs de toutes les DLL que votre programme utilise et une clé de texte unique pour chaque adresse de base. Pour spécifier une adresse de base à l’aide d’un fichier réponse, utilisez un signe arobase (**\@**) suivie du nom du fichier réponse, *filename*, suivi par une virgule, puis le *clé*valeur pour l’adresse de base à utiliser dans le fichier. L’éditeur de liens recherche *nom de fichier* dans le chemin spécifié, ou si aucun chemin d’accès n’est spécifié, dans les répertoires spécifiés dans la variable d’environnement LIB. Chaque ligne dans *filename* représente une DLL et présente la syntaxe suivante :

> *key* *address* [*size*] **;** *comment*

Le *clé* est une chaîne de caractères alphanumériques et n’est pas sensible à la casse. Il s’agit généralement du nom d’une DLL, mais ne sont pas nécessairement. Le *clé* est suivie d’une base de *adresse* dans la notation en langage C, hexadécimale ou décimale et une valeur maximale facultative *taille*. Les trois arguments sont séparés par des espaces ou des tabulations. L’éditeur de liens émet un avertissement si le texte spécifié *taille* est inférieur à l’espace d’adressage virtuel requis par le programme. Un *commentaire* est spécifié par un point-virgule (**;**) et peut être sur le même ou sur une ligne distincte. L’éditeur de liens ignore tout le texte du point-virgule à la fin de la ligne. Cet exemple montre une partie de ce type de fichier :

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

Si le fichier qui contient ces lignes s’appelle DLLS.txt, la commande suivante s’applique à ces informations :

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

Une autre consiste à définir l’adresse de base à l’aide de la *BASE* argument dans un [nom](name-c-cpp.md) ou [bibliothèque](library.md) instruction. L’option /BASE et [/DLL](dll-build-a-dll.md) options réunies sont équivalentes à la **bibliothèque** instruction.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **avancé** page de propriétés.

1. Modifier le **adresse de Base** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
