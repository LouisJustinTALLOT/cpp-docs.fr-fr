---
title: MASM pour x64 (ml64.exe) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe21bcb574c35827b07288dcae16e7ec9e1533d5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687673"
---
# <a name="masm-for-x64-ml64exe"></a>MASM pour x64 (ml64.exe)

Visual Studio inclut 32 bits et 64 bits des versions hébergées de Microsoft Assembler (MASM) à cibler x64 le code. Nommé ml64.exe, il s’agit de l’assembleur qui accepte x64 langue de l’assembleur. Les outils de ligne de commande MASM sont installés lorsque vous choisissez une charge de travail C++ lors de l’installation de Visual Studio. Les outils MASM ne sont pas disponibles en téléchargement séparé. Pour obtenir des instructions sur la façon de télécharger et installer une copie de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio). Si vous ne souhaitez pas installer l’IDE de Visual Studio terminée, mais souhaitez uniquement que les outils de ligne de commande, téléchargez le [Build Tools pour Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Utiliser MASM pour générer le code pour x64 cible sur la ligne de commande, vous devez utiliser une invite de commandes développeur pour x64 cibles, qui définit le chemin d’accès requise et les autres variables d’environnement. Pour plus d’informations sur la façon de démarrer une invite de commandes développeur, consultez [code de génération C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md).

Pour plus d’informations sur les options de ligne de commande ml64.exe, consultez [ML et référence de ligne de commande ML64](../../assembler/masm/ml-and-ml64-command-line-reference.md).

Assembleur inline ou utilisation du mot-clé ASM n’est pas pris en charge pour x64 ou les cibles ARM. Pour porter votre x86 code ce assembleur inline d’utilise x64 ou ARM, vous pouvez convertir votre code en C++, utiliser des fonctions intrinsèques du compilateur ou créer des fichiers sources du langage assembleur. Le compilateur Visual C++ prend en charge les fonctions intrinsèques afin que vous puissiez utiliser les instructions de la fonction spéciale, pour exemple, privilégié, bit analyse et de test, à blocage et ainsi de suite, dans en tant que proche de manière inter-plateformes que possible. Pour plus d’informations sur les fonctions intrinsèques disponibles, consultez [intrinsèques du compilateur](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Ajouter un fichier en langage assembleur à un projet Visual C++

Le système de projet Visual Studio prend en charge les fichiers en langage assembleur générés à l’aide de MASM dans vos projets C++. Vous pouvez créer x64 source du langage assembleur fichiers et de les créer dans des fichiers de l’objet à l’aide de MASM, qui prend en charge x64 entièrement. Vous pouvez ensuite lier ces fichiers de l’objet à votre code C++ conçu pour x64 cibles. Il s’agit d’une façon de contourner l’absence d’un x64 assembleur inline.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Pour ajouter un fichier en langage assembleur à un projet Visual C++ existant

1. Sélectionnez le projet dans **l’Explorateur de solutions**. Dans la barre de menus, choisissez **projet**, **personnalisations de la Build**.

1. Dans le **Visual C++ générer les fichiers de personnalisation** boîte de dialogue zone, cochez la case à cocher en regard **masm(.targets,.props)**. Choisissez **OK** pour enregistrer votre sélection et fermer la boîte de dialogue.

1. Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **fichier C++ (.cpp)** dans le volet central. Dans le **nom** contrôle d’édition, entrez un nouveau nom de fichier qui a un **.asm** extension au lieu de .cpp. Choisissez **ajouter** pour ajouter le fichier à votre projet et de fermer la boîte de dialogue.

Créez votre code en langage assembleur dans le fichier .asm que vous avez ajouté. Lorsque vous générez votre solution, l’assembleur MASM est appelé pour assembler le fichier .asm dans un fichier objet qui est ensuite lié à votre projet. Pour faciliter l’accès aux symboles, déclarez vos fonctions d’assembleur `extern "C"` dans votre code source C++, au lieu d’utiliser le C++ nommez les conventions de décoration dans votre langage assembleur fichiers sources.

## <a name="ml64-specific-directives"></a>Directives spécifiques ml64

Vous pouvez utiliser les directives spécifiques ml64 suivantes dans votre code source en langage assembleur qui cible x64 :

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

En outre, le [PROC](../../assembler/masm/proc.md) directive a été mis à jour pour une utilisation avec ml64.exe.

## <a name="32-bit-address-mode-address-size-override"></a>Mode d’adressage 32 bits (adresse taille remplacement)

MASM émet le remplacement de taille 0 x 67 adresse si un opérande de mémoire inclut des registres 32 bits. Par exemple, les exemples suivants provoquent le remplacement de taille d’adresse à émettre :

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM part du principe que si un déplacement 32 bits apparaît seul comme un opérande de mémoire, adressage 64 bits est destinée. Il n’existe actuellement aucune prise en charge pour l’adressage de 32 bits avec ces opérandes.

Enfin, la combinaison des tailles de s’inscrire dans un opérande de mémoire, comme illustré dans le code suivant, génère une erreur.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>