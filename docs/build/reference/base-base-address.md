---
description: En savoir plus sur:/BASE (adresse de base)
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
ms.openlocfilehash: 269911c7d9fce47be1b9755ddebf38170ea4e81c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182773"
---
# <a name="base-base-address"></a>/BASE (Adresse de base)

Spécifie l’adresse de base d’un programme.

## <a name="syntax"></a>Syntaxe

> **/Base :**{*adresse*[**,**<em>taille</em>] | **\@** <em>nom de fichier</em>**,**<em>clé</em>}

## <a name="remarks"></a>Notes

> [!NOTE]
> Pour des raisons de sécurité, Microsoft vous recommande d’utiliser l’option [/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) au lieu de spécifier des adresses de base pour vos fichiers exécutables. Cela génère une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement à l’aide de la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) de Windows. L’option/DYNAMICBASE est activée par défaut.

L’option/BASE définit une adresse de base pour le programme, en remplaçant l’emplacement par défaut d’un fichier. exe ou DLL. L’adresse de base par défaut d’un fichier. exe est 0x400000 pour les images 32 bits ou 0x140000000 pour les images 64 bits. Pour une DLL, l’adresse de base par défaut est 0x10000000 pour les images 32 bits ou 0x180000000 pour les images 64 bits. Sur les systèmes d’exploitation qui ne prennent pas en charge la randomisation du format d’espace d’adresse (ASLR), ou lorsque l’option/DYNAMICBASE : NO était définie, le système d’exploitation tente d’abord de charger un programme à son adresse de base spécifiée ou par défaut. Si l’espace disponible n’est pas suffisant, le système déplace le programme. Pour empêcher le réadressage, utilisez l’option [/fixed](fixed-fixed-base-address.md) .

L’éditeur de liens émet une erreur si l' *adresse* n’est pas un multiple de 64 Ko. Vous pouvez éventuellement spécifier la taille du programme. l’éditeur de liens émet un avertissement si le programme ne peut pas être contenu dans la taille que vous avez spécifiée.

Sur la ligne de commande, vous pouvez également spécifier l’adresse de base à l’aide d’un fichier réponse d’adresse de base. Un fichier de réponse d’adresse de base est un fichier texte qui contient les adresses de base et des tailles facultatives de toutes les dll que votre programme utilise, ainsi qu’une clé de texte unique pour chaque adresse de base. Pour spécifier une adresse de base à l’aide d’un fichier réponse, utilisez un arobase ( **\@** ) suivi du nom du fichier réponse, *nom* de fichier, suivi d’une virgule, puis de la valeur de *clé* de l’adresse de base à utiliser dans le fichier. L’éditeur de liens recherche le *nom de fichier* dans le chemin d’accès spécifié, ou si aucun chemin d’accès n’est spécifié, dans les répertoires spécifiés dans la variable d’environnement lib. Chaque ligne du *nom de fichier* représente une dll et utilise la syntaxe suivante :

>  *adresse* clé [*taille*] **;** *Commentaire*

La *clé* est une chaîne de caractères alphanumériques et ne respecte pas la casse. Il s’agit généralement du nom d’une DLL, mais il n’est pas nécessaire. La *clé* est suivie d’une *adresse* de base en langage C, hexadécimal ou notation décimale, et d’une *taille* maximale facultative. Les trois arguments sont séparés par des espaces ou des tabulations. L’éditeur de liens émet un avertissement si la *taille* spécifiée est inférieure à l’espace d’adressage virtuel requis par le programme. Un *Commentaire* est spécifié par un point-virgule (**;**) et peut être sur la même ligne ou sur une ligne distincte. L’éditeur de liens ignore tout le texte du point-virgule jusqu’à la fin de la ligne. Cet exemple montre une partie d’un fichier de ce type :

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

Si le fichier qui contient ces lignes est appelé DLLS.txt, l’exemple de commande suivant applique ces informations :

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

Une autre façon de définir l’adresse de base consiste à utiliser l’argument de *base* dans une instruction [Name](name-c-cpp.md) ou [Library](library.md) . Les options/BASE et [/dll](dll-build-a-dll.md) ensemble sont équivalentes à l’instruction **Library** .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Modifiez la propriété **adresse de base** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
