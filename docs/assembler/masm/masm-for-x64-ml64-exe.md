---
description: 'En savoir plus sur : MASM pour x64 (ml64.exe)'
title: MASM pour x64 (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 58970f65fbd98b4cbebae0a36c615cb380ec5b75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129725"
---
# <a name="masm-for-x64-ml64exe"></a>MASM pour x64 (ml64.exe)

Visual Studio comprend à la fois des versions 32 bits et 64 bits de Microsoft assembler (MASM) pour cibler le code x64. Nommé ml64.exe, il s’agit de l’assembleur qui accepte le langage assembleur x64. Les outils en ligne de commande MASM sont installés lorsque vous choisissez une charge de travail C++ lors de l’installation de Visual Studio. Les outils MASM ne sont pas disponibles en tant que téléchargement distinct. Pour obtenir des instructions sur le téléchargement et l’installation d’une copie de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio). Si vous ne souhaitez pas installer l’intégralité de l’IDE de Visual Studio, mais que vous souhaitez uniquement les outils en ligne de commande, téléchargez les [outils de génération pour Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Pour utiliser MASM afin de générer du code pour les cibles x64 sur la ligne de commande, vous devez utiliser une invite de commandes développeur pour les cibles x64, qui définit le chemin d’accès requis et d’autres variables d’environnement. Pour plus d’informations sur le démarrage d’une invite de commandes développeur, consultez [générer du code C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md).

Pour plus d’informations sur ml64.exe options de ligne de commande, consultez [ml et ML64 Command-Line référence](ml-and-ml64-command-line-reference.md).

L’assembleur inline ou l’utilisation du mot clé ASM n’est pas pris en charge pour les cibles x64 ou ARM. Pour porter votre code x86 qui utilise l’assembleur inline vers x64 ou ARM, vous pouvez convertir votre code en C++, utiliser des intrinsèques du compilateur ou créer des fichiers sources assembleur-langage. Le compilateur Microsoft C++ prend en charge les fonctions intrinsèques pour vous permettre d’utiliser des instructions de fonction spéciale, par exemple Privileged, Scan-bit/test, dislocked, etc., de la manière la plus proche possible d’une plateforme multiplateforme. Pour plus d’informations sur les intrinsèques disponibles, consultez [intrinsèques du compilateur](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Ajouter un fichier assembleur-langage à un projet Visual Studio C++

Le système de projet Visual Studio prend en charge les fichiers assembleur-langage générés à l’aide de MASM dans vos projets C++. Vous pouvez créer des fichiers sources de langage assembleur x64 et les générer dans des fichiers objets à l’aide de MASM, qui prend entièrement en charge x64. Vous pouvez ensuite lier ces fichiers objets à votre code C++ généré pour les cibles x64. Il s’agit d’une façon de surmonter l’absence d’un assembleur en ligne x64.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Pour ajouter un fichier assembleur-langue à un projet Visual Studio C++ existant

1. Sélectionnez le projet dans **l’Explorateur de solutions**. Dans la barre de menus, choisissez **projet**, **créer des personnalisations**.

1. Dans la boîte de dialogue **Visual C++ les fichiers de personnalisation** de la build, cochez la case en regard de **MASM (. targets,. props)**. Choisissez **OK** pour enregistrer votre sélection et fermer la boîte de dialogue.

1. Dans la barre de menus, choisissez **projet**, **Ajouter un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier C++ (. cpp)** dans le volet central. Dans le contrôle d’édition de **nom** , entrez un nouveau nom de fichier qui a une extension **. asm** au lieu de. cpp. Choisissez **Ajouter** pour ajouter le fichier à votre projet et fermer la boîte de dialogue.

Créez votre code assembleur-langue dans le fichier. asm que vous avez ajouté. Quand vous générez votre solution, l’assembleur MASM est appelé pour assembler le fichier. asm dans un fichier objet qui est ensuite lié à votre projet. Pour faciliter l’accès aux symboles, déclarez vos fonctions d’assembleur comme `extern "C"` dans votre code source c++, plutôt que d’utiliser les conventions de décoration de nom c++ dans vos fichiers sources assembleur-langue.

## <a name="ml64-specific-directives"></a>Directives spécifiques à ml64

Vous pouvez utiliser les directives spécifiques à ml64 suivantes dans votre code source assembleur-langue qui cible x64 :

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

En outre, la directive [proc](proc.md) a été mise à jour pour être utilisée avec ml64.exe.

## <a name="32-bit-address-mode-address-size-override"></a>32-mode d’adresse bits (remplacement de la taille d’adresse)

MASM émet la substitution de taille d’adresse 0x67 si un opérande de mémoire comprend des registres 32 bits. Par exemple, les exemples suivants entraînent l’émission de la valeur de remplacement de la taille d’adresse :

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM suppose que si un déplacement 32 bits apparaît seul comme un opérande de mémoire, l’adressage 64 bits est prévu. Il n’existe actuellement aucune prise en charge pour l’adressage 32 bits avec de tels opérandes.

Enfin, la combinaison de tailles de registres au sein d’un opérande de mémoire, comme illustré dans le code suivant, génère une erreur.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Voir aussi

[Référence de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)
