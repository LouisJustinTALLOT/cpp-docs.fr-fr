---
title: Multithreading à l’aide de C et Win32 | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09397b5a60dcc2cbe2b3e6265f6080f3c5c1e212
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428094"
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading à l'aide de C et de Win32

Microsoft Visual C++ prend en charge la création d’applications multithread. Vous devez envisager d’utiliser plusieurs threads si votre application doit effectuer les opérations coûteuses qui provoquent l’interface utilisateur de ne plus répondre.

Avec Visual C++, il existe deux façons de programme avec plusieurs threads : utiliser la bibliothèque Microsoft Foundation classes (MFC) ou de la bibliothèque Runtime C et de l’API Win32. Pour plus d’informations sur la création d’applications multithread avec MFC, consultez [Multithreading à l’aide de C++ et MFC](multithreading-with-cpp-and-mfc.md) après avoir lu les rubriques suivantes consacrées au multithreading en langage C.

Ces rubriques expliquent les fonctionnalités de Visual C++ qui prennent en charge la création de programmes multithread.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Ce que le multithreading est sur](multithread-programs.md)

- [Prise en charge de la bibliothèque pour le multithreading](library-support-for-multithreading.md)

- [Fichiers Include pour le multithreading](include-files-for-multithreading.md)

- [Fonctions de la bibliothèque Runtime C pour le contrôle du thread](c-run-time-library-functions-for-thread-control.md)

- [Exemple de programme multithread en C](sample-multithread-c-program.md)

- [Écriture d’un programme Win32 Multithread](writing-a-multithreaded-win32-program.md)

- [Compilation et liaison de programmes multithread](compiling-and-linking-multithread-programs.md)

- [Comment éviter les programmes multithread](avoiding-problem-areas-with-multithread-programs.md)

- [Stockage local des threads (TLS)](thread-local-storage-tls.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge du multithreading pour le code plus ancien (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)